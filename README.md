# ConfigFile
the config file is a txt file used to stablish parameters and configuration into the software without the needing of recompiling it whenever these configurations are changed.

This is an example of how is structured the configfile:
Example 1:

!MQTT
-host = localhost
-port = 1883
-protocol = tcp
-topic  = test
-clientID = ssss

!DB
-file = /path/to/my/sqlite/dbfile.db
Example 2:

!MQTT
-host = localhost
-port = 1883
-protocol = tcp
-topic = test
-clientID = ssss
-user = exampleUser
-password = examplePassword

!MYSQL
-host = localhost
-user = user
-password = password
The file is separeted in two type of information:

Groups: are denoted with a "!" before its name, is useful to split parameters and makes posible to have
parameters with the same name in different groups.
Parameters: are denoted with a "-" sufix, is the name the program will look for and get its value after the "=" simbol

## Config class

THe constructor just accepts one parameter and it is the path to the config file. Example:
```C++
Config _file("./config.txt");
```

Following the Example 2 showed before, if the user wants to look for the MQTT broker host would be in this form:

```C++
std::string _host = _file.GetConfigValue("MQTT", "host");
```

