# Flyway-migrations
This repository includes an example of how to build a custom Flyway image to perform database migrations using containers.


## Note

* Make sure to update the *flyway.conf* file to point your target database
* Make sure to check the paths for both Configuration file and SQL Scripts

## Intructions
### Build custom Flyway image
```docker
docker build . -t flyway-migrations
````

### Set $ConfigFile and $SQLScripts
```bash
ConfigFile=./ConfigFile;
SQLScripts=./SQLScripts;
```
### Perform migrations
```docker
# Check migrations info
docker container run --rm \
    --volume $ConfigFile:/flyway/conf \
    --volume $SQLScripts:/flyway/sql \
    --network host \
    flyway/flyway info
    
# Perform migrations
docker container run --rm \
    --volume $ConfigFile:/flyway/conf \
    --volume $SQLScripts:/flyway/sql \
    --network host \
    flyway/flyway migrate
```

## Questions?
If you have questions or comments about this demo, don't hesitate to contact me at <crobles@dbamastery.com>

## Follow me
[![N|Solid](http://dbamastery.com/wp-content/uploads/2018/08/if_twitter_circle_color_107170.png)](https://twitter.com/dbamastery) [![N|Solid](http://dbamastery.com/wp-content/uploads/2018/08/if_github_circle_black_107161.png)](https://github.com/dbamaster) [![N|Solid](http://dbamastery.com/wp-content/uploads/2018/08/if_linkedin_circle_color_107178.png)](https://www.linkedin.com/in/croblesdba/) [![N|Solid](http://dbamastery.com/wp-content/uploads/2018/08/if_browser_1055104.png)](http://dbamastery.com/)
