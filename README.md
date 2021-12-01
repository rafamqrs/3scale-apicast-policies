# 3Scale Reverse Proxy - URL Rewriting
On this repository you will find the two differents configurations:
1. First show you how to setup 1:1 Product and Backend with differents paths.
2. Second show you how to setup 1:N Product and Backends.

### URL Rewriting

The URL Rewriting policy allows you to modify the path of a request and the query string.

When combined with the 3scale APIcast policy, if the URL Rewriting policy is placed before the APIcast policy in the policy chain, the APIcast mapping rules will apply to the modified path. If the URL Rewriting policy is placed after APIcast in the policy chain, then the mapping rules will apply to the original path.

The policy supports the following two sets of operations:

commands: List of commands to be applied to rewrite the path of the request.
query_args_commands: List of commands to be applied to rewrite the query string of the request.



