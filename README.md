<p align="center"> <img src="https://raw.githubusercontent.com/qeeqbox/xslt-injection/main/content/xslt-injection.svg"></p>

## XSLT Injection
XSLT Injection is a security vulnerability that arises when untrusted input is incorporated into an XSLT stylesheet or otherwise influences the XSLT transformation in an unsafe manner. If an attacker can manipulate parts of the stylesheet, they may alter the transformation process and, depending on the specific XSLT processor and its configuration, access external resources or perform unauthorized operations.

XSLT (Extensible Stylesheet Language Transformations) is a language used to transform XML documents into various formats, such as HTML, plain text, or additional XML documents.

In standard XSLT processing, user data is treated as data. However, XSLT injection occurs when untrusted input is treated as part of the XSLT code or stylesheet structure.

## How XSLT Injection Works
1. Untrusted Input Influences the Stylesheet: An application accepts user-controlled input and directly incorporates it into an XSLT stylesheet or dynamically constructs XSLT code using that input.
2. Insufficient Separation Between Code and Data: Instead of passing user input as an XSLT parameter or variable, the application inserts the input into the stylesheet itself.
3. XSLT Processing: The XSLT processor then interprets the resulting stylesheet. If the attacker has successfully modified the stylesheet, the processor may execute operations that the application developer did not intend.

## XSLT Injection Impact
- Data Disclosure: An attacker may gain access to XML data or other information exposed to the XSLT processor.
- Unauthorized Resource Access: If external resource access is enabled, an attacker might cause the processor to access resources that were not intended to be exposed.
- Denial of Service: Maliciously constructed XSLT transformations can consume excessive CPU or memory resources, potentially affecting the application's availability.
- Server-Side Code Execution: Some XSLT processors provide extension functions or integrations that can interact with the operating system or other services. If these capabilities are enabled and accessible to an attacker, XSLT injection may lead to arbitrary code execution. However, code execution is not an inherent risk associated with XSLT injection; it depends on the specific processor, available extensions, and security configuration.

## XSLT Injection Mitigation
- Keep XSLT Code Separate From User Input: Do not construct XSLT stylesheet source code using untrusted input. Instead, maintain a static stylesheet and pass user-controlled values through XSLT parameters or variables.
- Use XSLT Parameters: Treat user input as data rather than code. This usage prevents the value from becoming part of the stylesheet structure.
- Restrict External Resource Access
- Use a Restricted XSLT Processor Configuration: Configure the XSLT processor with the minimum capabilities necessary for the application. Where possible, use access-control mechanisms or sandboxing to prevent unauthorized file and network access.
- Validate Input Where Appropriate: Input validation can provide an additional layer of defense, but it should not be the primary protection. The key defense is to prevent untrusted input from becoming part of the XSLT stylesheet itself.
- Apply the Principle of Least Privilege: Run the application and XSLT processor with only the permissions needed. Restrict access to sensitive files, network resources, and operating system functionality.
- Keep XSLT Processors Updated: Use supported versions of XSLT libraries and processors, applying security updates regularly.
Perform Security Testing: Conduct code reviews and security testing to determine if user-controlled input can influence XSLT stylesheets or access restricted processor capabilities.


## XSLT Injection Example
Clone this current repo recursively
```sh
git clone --recurse-submodules https://github.com/qeeqbox/xslt-injection
```
Run the webapp using Python
```sh
python3 xslt-injection/vulnerable-web-app/webapp.py
```
Open the webapp in your browser 127.0.0.1:5142
<p align="center"> <img src="https://raw.githubusercontent.com/qeeqbox/xslt-injection/main/content/1.png"></p>
Use the default credentials (username: admin and password: admin) to login
<p align="center"> <img src="https://raw.githubusercontent.com/qeeqbox/xslt-injection/main/content/2.png"></p>

## Code
When the user enters a hostname or IP to check their network connectivity, the webapp calls the add_ping() function. This function uses the internal ping OS command, the dynamic value from the user can contain a malicious payload that also gets executed by the host
```py
```

