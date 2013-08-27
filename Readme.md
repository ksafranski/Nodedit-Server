# Nodedit Server

The Nodedit-Server runs on your remote machine to provide the API for access via the [Nodedit Client](https://www.github.com/Fluidbyte/Nodedit).

## Usage & Requirements

The server requires [NodeJS](http://www.nodejs.org) as well as the restify and fs-extra plugins. The entire package can easily be installed by cloning this repository to your server and then 
running `npm install`.

To configure the server, simply open the `server.js` file and edit the `config` object:

```
var config = {
    // Authentication keys
    keys: [
        "12345",
        "67890"
    ],
    /**
     * Allowed IP's or ranges
     * Can use * for wildcards, *.*.*.* for no restrictions
     */
    ips: [
        "*.*.*.*"
    ],
    /**
     * SSL Config
     * Set key and cert to absolute path if SSL used, false if not
     */
    ssl: {
        key: false,
        cert: false
    },
    // Port designation
    port: 8080,
    // Base directory
    base: "path/to/root",
    // Default create mode
    cmode: "0755"
};
```

Once configured, simply run via `node server.js` or you can install the node-forever plugin `npm install -g forever` which will allow you to run the server more permanently via 
`forever start server.js`.

Once the server is running you can connect the Nodedit client via the URL & Port and by specifying a Key.

## Arguments

You can pass in arguments when starting the `server.js` file. The following format is supported:

```
node server.js --base=workspace --port=1111 --cmode=0755
```

You can also pass in a config file containing a JSON formatted configuration via:

```
node server.js --config=config.json
```