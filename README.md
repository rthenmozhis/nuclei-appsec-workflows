## Nuclei Demos

#### CVE Exploit

* Download the exploit template

```bash
wget https://raw.githubusercontent.com/projectdiscovery/nuclei-templates/master/cves/2021/CVE-2021-41174.yaml
```

* Run Grafana docker

```bash
docker run -d --name=grafana -p 3000:3000 grafana/grafana-enterprise:8.1.0
```

* Exploit the vulnerability

```bash
nuclei -t CVE-2021-41174.yaml -u http://localhost:3000
```


#### GitHub workflow

##### Local test

* Run app

```bash
docker run -it -p 5050:5050 we45/vul_flask
```

* Test urls

```bash
http GET http://localhost:5050
```

* Test with nuclei template

```bash
nuclei -t api-scan.yaml -u http://localhost:5050
```

* Test for template injection

```bash
nuclei -t template-injection.yaml -u http://localhost:5050
```

##### References

* https://twitter.com/pdnuclei/status/1457121459399053316
* https://github.com/projectdiscovery/nuclei-templates/tree/master/cves/2021
* https://github.com/grafana/grafana/security/advisories/GHSA-3j9m-hcv9-rpj8
* https://nuclei.projectdiscovery.io/templating-guide/operators/matchers/
* https://blog.escape.tech/devsecops-part-iii-scanning-live-web-applications/