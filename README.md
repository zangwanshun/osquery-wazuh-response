## Introduction

Osquery extension to perform active response using sql query. The repo contains
wazuh active response .sh and .cmd files and some python scripts. 
Custom .sh,.cmd and .py can be added and hence can be remotely used by osquery. The 
extension is coded keeping security in mind. 

The core is just few lines of python codes.

## Execution

* `pip install osquery`
* `chmod +x active_response_extension.py`
* `sudo osqueryi --allow_unsafe --extension active_response_extension.py`


> Executing Wazuh responses

    select * from active_response where rule="host-deny.sh" and action="add" and ip="24.56.78.98"';

> Killing a process

    select * from active_response where rule="kill_process" and args='{"signal":"9","pid":56776}';
    
     
Wazuh require action,ip,user in order to execute the command.

> Create your own command in python. 

1. Refer kill_process.py structure
2. import the custom file
3. include filename in ActiveResonse.PYTHON_RULES.
4. In query add **args** as a json of arguments required.

Read more about it on [docs](https://docs.easysiem.com/agents/osquery/active-response-extensions)



## TODO

