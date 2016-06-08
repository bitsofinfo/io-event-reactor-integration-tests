# io-event-reactor-integration-tests

Sample integration test application for [io-event-reactor](https://github.com/bitsofinfo/io-event-reactor) and its plugin ecosystem

This is not available as NPM module. To use it, simple clone this repository, go the root of the project and type

```
npm install .
```

You can run the sample `io-event-reactor` instance by running it as follows (replace the parameters as appropriate). The database
you point to needs to permit the specified user the ability to drop/create tables:

```
node sampleIoReactor.js \
    --pathsToMonitor=/tmp/test1 /tmp/test2 \
    --triggeringEvents=add addDir unlink unlinkDir change \
    --triggeringRegex="(.*test\\d+.txt.*|.*bitsofinfo.*)" \
    --targetShellExecDir=/tmp/mytestdir \
    --mysqlHost=localhost \
    --mysqlUser=root \
    --mysqlPw=root \
    --mysqlDb=io_event_reactor
```

Once started this program will monitor the paths specified, and as matching events
occur entries will be made into the configured mysql database and the shell-exec plugin
will generate marker files in a unique path under the specified `targetShellExecDir` directory.
