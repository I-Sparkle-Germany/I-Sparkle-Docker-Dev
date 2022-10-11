# I-Sparkle-Docker-Dev

## Description

WISE development uses [Docker](https://www.docker.com/). Using Docker simplifies and standardizes the development environment so that developers can quickly and easily start developing WISE.

## Setup

1. Install Docker from [here](https://www.docker.com/products/docker-desktop). In the Docker preferences, set the RAM to at least 5GB.
2. In the same folder, checkout [I-Sparkle-Docker-Dev (this project)](https://github.com/I-Sparkle-Germany/I-Sparkle-Docker-Dev), [I-Sparkle-API](https://github.com/I-Sparkle-Germany/I-Sparkle-API), and [I-Sparkle-Client](https://github.com/I-Sparkle-Germany/I-Sparkle-Client).

```
$ git clone https://github.com/I-Sparkle-Germany/I-Sparkle-Docker-Dev
$ git clone https://github.com/I-Sparkle-Germany/I-Sparkle-API
$ git clone https://github.com/I-Sparkle-Germany/I-Sparkle-Client
$ ls
I-Sparkle-Docker-Dev
I-Sparkle-API
I-Sparkle-Client
```

3 Run `npm install` in I-Sparkle-Client directory

```
$ cd I-Sparkle-Client
I-Sparkle-Client $ npm install
```

4. Run `docker compose up` in the I-Sparkle-Docker-Dev directory

```
$ cd I-Sparkle-Docker-Dev
I-Sparkle-Docker-Dev $ docker compose up
```

5. Wait for everything to download, compile, and start. This can take a while depending on your computer and connection speeds. When you see this in the output, all of the application has started:

```
...
i-sparkle-client  | ** Angular Live Development Server is listening on 0.0.0.0:4200, open your browser on http://localhost:4200/ **
i-sparkle-client  |
i-sparkle-client  |
i-sparkle-client  | ✔ Compiled successfully.
```

1. When you see the above output in your log output, WISE will be running at http://localhost:81. Go there with your browser to load the I-Sparkle homepage.
2. Log in with admin/pass, or previewuser/wise.

Any changes that you make to the source code will be automatically compiled and reloaded in the browser.

## Main Docker commands

1. Start/Stop development containers

```
$ docker-compose [up/down]
```

2. List running containers

```
$ docker container ls
```

3. Restart container (ex: 'i-sparkle-client')

```
$ docker restart i-sparkle-client
```

4. Access container's command line (ex: 'i-sparkle-client')

```
$ docker exec -it i-sparkle-client sh
```

5. Run 'npm test' in i-sparkle-client container

```
$ docker exec -it i-sparkle-client npm test
```

6. Run 'npm test' in i-sparkle-client container with the watch option

```
$ docker exec -it i-sparkle-client npm test -- "--watch=true"
```

7. Run 'maven test' in i-sparkle-api container

```
$ docker exec -it i-sparkle-api mvn test
```

## MySQL Docker commands

1. Connect to MySQL container (password: iamroot)

```
$ docker run -it --network i-sparkle-docker-dev_default --rm mysql:8 mysql -hi-sparkle-mysql -uroot -p
```

2. Import data from mysqldump

```
$ docker exec -i i-sparkle-mysql sh -c 'exec mysql wise_database -uroot -p"$MYSQL_ROOT_PASSWORD"' < ~/path_to/wise_database_dump.sql
```

3. Dump data from MySQL container

```
$ docker exec -i i-sparkle-mysql sh -c 'exec mysqldump wise_database -uroot -p"$MYSQL_ROOT_PASSWORD"' > wise_database_dump.sql
```

# Resources

Open-source license: GNU General Public License, v3. See LICENSE.txt for details.

To see WISE in action and for inquiry science curricula developed by the WISE research team at UC Berkeley, visit https://wise.berkeley.edu.

Developer discussions: https://github.com/WISE-Community/WISE-Docker-Dev/discussions

General WISE discussions: https://wise-discuss.berkeley.edu/
