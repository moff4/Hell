# Hell  

Command line utility to controll daemons  

## Usage
```
 $ $0 [-h|-?|--help]
 $ $0 ctl <service_name> [ start | stop | restart | reload | status ]
 $ $0 conf <service_name> [ [ add | update ] [ -d=<dir> ] [ -c=<cmd> ] [ -e=<env_file> ] | delete | show ]
 Flags:
   -h , -? , --help
       See help message
 Flags for conf:
   add
        add new service to config
        must be also passed --cmd, --dir and --env
   update
        update service in config
        must be also passed --cmd, --dir or --env
   show
        show service's config
   delete
        delete service from config
 Args for conf:
   -c=<cmd> |--cmd=<cmd>
       command to be executed
   -d=<dir> |--dir=<dir>
       dir to be changed before executing
   -e=<env_file> |--env=<env_file>
       file with enviroment variables
 Flags for ctl:
   start, stop, restart
        Start/Stop/Restart service
   reload
        Reload configuration
   status
        Print current status
```

## Dependences:  
* [jshon](http://kmkeen.com/jshon) - command line json parser

## Configuration files

All configs are json objects  

### Services  

Services store data about each service  
key - service name  
value - object with three key:  
* cmd - command to start your service (required)  
* dir - path where to run command to start your service (required)  
* env - file name with full path (or path from "dir") to env-file. env-file - bash file that exports enviroment variables. (optional)  

Example:  
```json  
{  
	"MyService": {  
		"cmd": "python3 main.py",  
		"dir": "/path/to/project/dir/",  
		"env": "/path/to/env/file"  
	}  
}  
```  

### Pids

Internal config that keeps process ids  
Example:  
```json
{
	"MyService": 1234
}
```
