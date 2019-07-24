couchbase-build-container
-------------------------
couchbase-build-container is a simple 'docker-compose.yml' which aims to
improve the Couchbase development workflow on unsupported platforms.

Usage
-----
Dependencies:
 - docker
 - docker-compose

First of all ensure that the container is running.
```sh
docker-compose up -d # run the build container
docker exec it -u couchbase couchbase-build /bin/bash # access the shell for the container
```

Follow the build steps as written in the Couchbase [tlm](https://github.com/couchbase/tlm) repository.

Run the newly compiled version of Couchbase CE/EE.
```sh
./$COUCHBASE_BUILD_ROOT/install/bin/couchbase-server -- -kernel global_enable_tracing false -noinput
```

Determine the IP address of the build container
```sh
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' couchbase-build
```

Navigate to '$BUILD_CONTAINER_IP:8091' to access the web user interface for Couchbase Server.

License
-------
MIT License

Copyright (c) 2019 James Lee <jamesl33info@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
