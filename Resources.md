# Additional Resources on Agentic Workflows inspired by the Discussions in the class

## MCP Security and The Confused Deputy Problem

* [Securing MCP-based Agent Workflows, Grigoris Ntousakis et al, 2025](https://github.com/dimitarpg13/5-Day-AI-Agents-Intensive-Course-with-Google/blob/main/articles/MCP_security/Securing_MCP-based_Agent_Workflows_Ntousakis_2025.pdf)

* [Model Context Protocol (MCP): Understanding security risks and controls, Florencio Cano Gabarda, RedHat, July 2025](https://www.redhat.com/en/blog/model-context-protocol-mcp-understanding-security-risks-and-controls)

* [The complete guide to MCP security: How to secure MCP servers & clients, Maria Paktiti, August 2025](https://workos.com/blog/mcp-security-risks-best-practices)

* [How the ‘Confused Deputy Problem’ has made a comeback, Morey Haber, June 17, 2025](https://www.scworld.com/perspective/how-the-confused-deputy-problem-has-made-a-comeback)

* [The Confused Deputy (or why capabilities might have been invented), Norm Hardy, 1988](https://github.com/dimitarpg13/5-Day-AI-Agents-Intensive-Course-with-Google/blob/main/articles/MCP_security/The_Confused_Deputy_why_capabilities_might_have_been_invented_Hardy_1988.pdf)

* [Model Context Protocol has prompt injection security problems, Simon Willison, 2025, substack online article](https://simonw.substack.com/p/model-context-protocol-has-prompt)

* [Fortifying Your AWS Cloud Against Cross-Service Confused Deputy Attacks, Nehal Baviskar, Security QA Engineer, Cloud, Qualys, 2025](https://blog.qualys.com/vulnerabilities-threat-research/2025/07/24/fortifying-your-cloud-against-cross-service-confused-deputy-attacks)

* [Cross-service confused deputy prevention, Amazon Bedrock Agent Core doc, 2025](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/cross-service-confused-deputy-prevention.html)

* [GitHub MCP exploited: Accessing private repositories via MCP, HackerNews, 2025](https://news.ycombinator.com/item?id=44097390)

<ins>**_Note on the Confused Deupty Problem_**</ins>

The [confused deputy problem](https://en.wikipedia.org/wiki/Confused_deputy_problem) is a [privilege escalation vulnerability](https://en.wikipedia.org/wiki/Privilege_escalation) where a program (the "deputy") is tricked by a less-privileged entity into misusing its authority to perform an action it shouldn't. In the context of Model Context Protocol (MCP), this often happens when an MCP server, which has legitimate access to a user's resources (the deputy), is tricked by an attacker into executing commands or accessing data on the attacker's behalf. 

**How it applies to MCP**

 *  Acting on behalf of the user: An MCP server can act as a trusted "deputy" on behalf of a user to interact with other services, like a calendar or a cloud storage provider.

 *  Misused authority: If the MCP server is not properly implemented, it can be tricked into misusing its user-granted permissions. For example, a malicious client could trick a server into sending an email that it would not normally have access to send.

**Examples of misconfigurations:**

 *  OAuth issues: MCP servers that act as proxies in OAuth flows can be tricked into bypassing user consent screens if not configured correctly, allowing an attacker to get unauthorized access tokens.

 *  Tool shadowing: In some architectures, an attacker can register a malicious tool with the same name as a legitimate one on a different server. This tricks the MCP client into using its database credentials (the authority) on the malicious version of the tool instead of the legitimate one, say chrismartorella.ghost.io.

 *  Over-permissioned tokens: When the tokens provided to the MCP server have too many permissions, an attacker can leverage a vulnerable MCP implementation to access data or perform actions that the user would never have authorized.

**Consequences:**
The potential consequences include data breaches, unauthorized modifications, and other forms of abuse because a powerful tool is being used to perform malicious actions that it was not intended for, explains the Qualys Blog. 
