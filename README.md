# Service Probes
Collection of TCP/UDP probes for service detection.

## Probe file structure
```toml
[metadata]
name = "Some service probe"
description = "Description of the probe"
version = "1.0.0"
author = "Your Name"

[probe]
protocol = "tcp"                                        # Protocol to use for the probe
request = "GET / HTTP/1.1\r\nHost= example.com\r\n\r\n" # Request to send
rarity = 6                                              # Rarity of the probe on 1 to 9 scale
wait = 1000                                             # Wait time in milliseconds before sending the request, can be blank
ports = [80, 443]                                       # Ports to be checked, can be blank, if not specified, all ports should be checked

[matches.service-1]
regex = "HTTP/1.1 200 OK (.*)" # PCRE-styled regex
soft = true                    # Enable soft matching

# Matched service information
product_name = "$1"   # Can contain variables from regex groups
version = ""
info = ""
hostname = ""
operating_system = ""
device_type = ""
cpe = ""

[matches.service-2]
regex = "HTTP/1.1 404 Not Found"
```

## Contribution
All contributions are welcome! To contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch for your changes.
3. Make your changes and commit them.
4. Push your changes to your fork.
5. Create a pull request.
