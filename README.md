# gfwlist2surge
A simple tool to convert GFWList into surge config expressions.

```
Usage: main.py [-c CUSTOM.CONF] [-i GFWLIST] [-o SURGE.CONF] [-r]
    -c CUSTOM.CONF, --custom CUSTOM.CONF
        Optional argument for your own local custom domain list
    -i GFWLIST, --input GFWLIST
        Optional argument for local GFWList file (base64 encoded), default is tinylist
    -o SURGE.CONF, --output SURGE.CONF
        Optional argument for Surge config output, default is surge.conf
    -t, --tld
        Optional argument for updating top domain list
```

Automatically combine GFWList with your custom.conf (if provided), and generate surge.conf with uniquified and sorted domain list in the following format:

```
DOMAIN-SUFFIX,<domain0>
DOMAIN-SUFFIX,<domain1>
DOMAIN-SUFFIX,<domain2>
DOMAIN-SUFFIX,<domain3>
```

You may create a RULE-SET in Surge config file to quickly add these domains to your rules:

```
RULE-SET,https://raw.githubusercontent.com/flitpend/gfwlist2surge/master/surge.conf,<your_proxy>
```

Example 1: fetch tinylist from Github and convert to surge.conf
```sh
python3 main.py 
```
Example 2: merge tinylist and your custom domain list, then convert to surge.conf
```sh
python3 main.py -c custom.conf
```
Example 3: merge local gfwlist (base64 encoded) and your custom domain list, then convert to yourfilename.conf
```sh
python3 main.py -i gfwlist.txt -c custom.conf -o yourfilename.conf
```
Example 4: update tld.txt (top level domain)
```sh
python3 main.py -t
```
