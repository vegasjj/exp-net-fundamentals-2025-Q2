# Testing the Python webserver

## Start Server

You need to serve the `index.html` in the projects's root directory if you want to test the firewall rule before hand.

```sh
cd projects/windows-firewall-rules
python -m http.server 8000
```

## Curl server

Use `curl` to get the test webpage and confirm it loads correctly.

```sh
curl http://127.0.0.1:8000
```

Test the `curl` command from outside AWS to confirm the server is reacheable from the internet (replace the IP with the Elatic IP address)

## Proceed with deployment

Once the tests are successful repeat the steps with the actual Python app you need to deploy in the development environment.
