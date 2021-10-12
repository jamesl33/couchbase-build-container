couchbase-build-container
-------------------------
couchbase-build-container is a simple 'docker-compose.yml' which aims to improve the Couchbase development workflow on
unsupported platforms.

Usage
-----
Dependencies:
 - docker
 - docker-compose

First of all ensure that the container is running.
```sh
# When running with docker-compose V1
docker-compose up -d

# When running with docker-compose V2
docker compose up -d

# Access the shell for the container
docker exec it -u couchbase couchbase-build /bin/bash
```

Follow the build steps as written in the Couchbase [tlm](https://github.com/couchbase/tlm) repository using
`$HOME/Projects/couchbase-build` as the "source" directory.

Run the newly compiled version of Couchbase CE/EE.
```sh
# Change directory into the 'ns_server' directory
cd $HOME/Projects/couchbase-build/ns_server

# Run one or more modes using 'cluster_run'
./cluster_run --nodes 1 --dont-rename

# Connect the nodes into a cluster using 'cluster_connect'
./cluster_connect -n 1 -s 1024 -T n0:kv
```

Connect to the cluster using the WebUI by visiting `localhost:9000` in your chosen web browser, see the `cluster_run`
and `cluster_connect` scripts for more information about how the ports are configured for multiple nodes.

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
