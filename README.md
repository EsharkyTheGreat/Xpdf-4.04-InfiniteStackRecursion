# POC for Xpdf 4.04 Infinite Stack Recursion 

This Repo contains crafted pdfs which trigger multiple vulnerabilities in Xpdf v4.04 which causes an infinite stack recursion. Any attacker could use this vulnerability to cause a DoS attack if the binary was running as a service. This is similar to CVE-2019-13288


### POC
Run any of the crashing files labelled crash0 to crash16 with the `pdftotext` binary.
```bash
pdftotext ./crash0
pdftotext ./crash1
...
pdftotext ./crash16
```

### Vulnerability Discovery
This vulnerability was discoverd with the help of AFL++

### Root Cause
This vulnerability is due to an infinite stack recursion in the multiple functions like  `Catalog::countPageTree(Object *pagesObj)` , `XRefCacheEntry::XRefCacheEntry`, `Stream::Stream`, `Object::Object`
