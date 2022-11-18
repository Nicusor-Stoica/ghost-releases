## Ghost

#### Command line usage :

Help : `./ghost --help`

A single domain : `./ghost start -h www.qualitystreet.co.uk -t http://localhost:3000`

A single domain on custom ports : `./ghost start -h www.qualitystreet.co.uk -t http://localhost:3000 --http 8080 --https 8084`

From configuration file `./ghost config custom-ports.ghostconfig.json`

From config file stored in the working directory  `./ghost config` ; It will automatically scan for a config file. If more than one config file is found, ghost will shut down.
#### Help

If you are having problems visiting {host} please follow these steps :

On Chrome :
1. Open chrome://flags/#allow-insecure-localhost
2. Enable it
3. Open chrome://flags/#enable-async-dns
4. Disabled it
5. Open chrome://net-internals/#hsts
6. Go to Delete domain security policies and fill it with {virtual_host}
7. Press Delete
8. Restart Chrome (optional)
9. If the issue persists, try using a new profile or incognito or start Chrome with the --ignore-certificate-errors flag

On Firefox :
1. Open bout:config
2. In the search box above the list, type or paste enterp and pause while the list is filtered
3. Double-click the security.enterprise_roots.enabled preference to switch the value (if false set true, if true set false)
4. Open the full History window with the keyboard shortcut Ctrl + Shift + H
5. Find the site you want to delete the HSTS settings for - you can search for the site at the upper right if needed.
6. Right-click the site from the list of items and click Forget About This Site.This should clear the HSTS settings (and other cache data) for that domain.
7. Restart Firefox and visit the site. (optional)
8. If the issue persists, try using incognito


#### JSON Configuration

Ghost supports JSON configuration as follows :

```json
[
  {
    "virtual_host": "www.qualitystreet.co.uk",
    "target_host": "http://localhost:3000",
    "http_port": 8080,
    "https_port": 8084,
    "append_headers": {
      "x-store-id": "62b30eed7e1596001a36f3a3",
      "x-store-name": "stoica09may"
    }
  }
]
```

Where :

1. `virtual_host` represents the host that you want to emulate on localhost
2. `target_host` represents the host to proxy to that runs on your PC
3. `http_port` represents the insecure port for your virtual host
4. `https_port` represents the secure port for your virtual host
5. `append_headers` holds a set of headers to be forwarded to your target host

#### Socks v5 server

Share your socks5 server in order for other developers to access your virtual host, you will need to port forward the socks port.

In order for this to work they will need to use your SOCKS server and instruct the browser to perform DNS over SOCKS5 (where possible; FireFox recommended).
