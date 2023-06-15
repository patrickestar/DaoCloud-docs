# Configuring Domain name Policies

The micro-service gateway provides the domain name level policy configuration capability. After a domain name level policy is configured, you do not need to configure policies for multiple apis under the same domain name. Currently, two domain-level policies are supported: cross-domain and local traffic limiting.

You can configure domain name policies in either of the following ways:

- For details about how to set policies when creating domain names, see [Add Domain](add-domain.md).
- After the domain name is created, run the [Change Domain](update-domain.md) command to adjust the domain name.

The cross-domain and local traffic limiting policies are described as follows:

## Local current limiting

After you configure local traffic limiting for a domain name, the configuration is automatically applied to all apis that use the domain name.

For details about configuring local traffic limiting, see [Local Rate Limit](../api/api-policy.md#_6).

!!! note


## cross-domain

<! -- To be added: Explain what is cross-domain, cross-domain functions, effects, etc. -->

Note the following when filling in the configuration:

- Enable credentials: After this is enabled, cross-domain requests need to be checked for credentials. After the check is passed, the cross-domain request can be processed.
- Allowed request method: Select the HTTP request mode. See the official W3C document [Name Method Definitions](https://www.rfc-editor.org/rfc/rfc9110.html#name-method-definitions) for detailed instructions on the various request methods.
- Allowable request sources: Limit multiple specific request sources, usually using IP.
- Pre-check duration: indicates the duration of checking credentials and request methods before processing cross-domain requests. The unit of time is seconds, minutes, and hours.
- Allowable request headers: Qualifies specific HTTP request header keywords. After the keyword is added, the corresponding keyword must be added to the request header to access the target service.
- Exposed request header: Controls the exposed request header keyword. Multiple values can be configured.

    <!--![]()screenshots-->