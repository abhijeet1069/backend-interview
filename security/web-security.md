# Web Security

## Authentication

Authentication is who are you?

## Authorization

Authorization is what you are allowed to do?

## Common webapp vulnerabilities

### Broken Authentication

Broken authentication occurs when an application fails to verify user's identity securely
or manages authentication credentials incorrectly.

An attacker might gain access to another user’s account by exploiting weaknesses in the 
authentication process.

Common causes:

* Weak passwords or missing password policies
* No protection against repeated login attempts
* Poor password storage practices
* Insecure password reset mechanisms
* Predictable or improperly validated authentication tokens
* Improper session management

Prevention:

* Hash passwords using a suitable password hashing algorithm such as Bcrypt or Argon2
* Implement rate limiting or throttling for repeated login attempts
* Use MFA where appropriate
* Implement secure password reset flows
* Use established authentication frameworks rather than inventing your own
* Protect authentication tokens and credentials in transit using HTTPS 

### Session Fixation

Session fixation occurs when an atttacker causes a victim to authenticate using a session
identifier that an attacker already knows.

If the application continues using that session identifier after login, the attacker 
may be able to use it to access the victim’s authenticated session.

Prevention:
* Regenerate the session identifier after successful authentication

### Cross site scripting

Cross-site scripting occurs when an attacker injects malicious client-side content into a page 
that is viewed by another user.
The browser executes the injected script in the security context of the vulnerable website.
This can allow attackers to manipulate page content, perform actions as the victim, or steal 
accessible information.

Prevention:

* Apply context*appropriate output encoding.
* Avoid inserting untrusted content using unsafe JavaScript APIs such as innerHTML.
* Use safe templating practices.
* Sanitize HTML when users genuinely need to submit permitted HTML.
* Consider a Content Security Policy (CSP) as an additional defense.

### Cross site request forgery

CSRF occurs when an attacker tricks an authenticated user’s browser into sending an unwanted 
request to an application.

The attack is particularly relevant when the application authenticates users using cookies 
that browsers automatically attach to requests.

Prevention

* Use CSRF tokens for state-changing requests when appropriate.
* Configure cookie attributes such as SameSite as an additional defense.
* Validate request origins where appropriate.
* Do not use GET requests for operations that change application state.

### Injections

Injection vulnerabilities occur when an application treats untrusted input as part of a command,
query, or executable expression.

Common examples include:

* SQL injection.
* Command injection.
* LDAP injection.
* Expression Language injection.

### Sensetive Data Exposure

Sensitive data exposure occurs when an application fails to adequately protect confidential information.

Examples include:

* Passwords.
* Authentication tokens.
* Personal information.
* Financial records.
* Session identifiers.
* API keys.
* Database credentials.

Prevention:

* Use HTTPS.
* Hash passwords with a suitable password-hashing algorithm.
* Encrypt sensitive data at rest when appropriate.
* Keep secrets out of source code and logs.
* Restrict access to confidential data.
* Minimize the amount of sensitive information stored and returned.
* Use appropriate key-management practices.

### Lack of method access control

This occurs when an application fails to restrict sensitive operations to authorized users.
A user may be authenticated but still lack permission to perform a particular action.
This is an authorization problem, not an authentication problem.

Prevention:

* Define authorization rules for sensitive operations.
* Enforce access control on the server.
* Check resource ownership where appropriate.
* Apply the principle of least privilege.
* Test both permitted and forbidden access.

### Using dependencies with known vulnerabilities

Applications rely on external libraries and frameworks to provide functionality.

A dependency may contain a known security vulnerability. If your application uses an 
affected version in a vulnerable configuration, attackers may be able to exploit it.

Prevention:

* Regularly scan project dependencies for known vulnerabilities.
* Upgrade to supported, patched versions.
* Use maintained frameworks and libraries.
* Remove unnecessary dependencies.
* Monitor security advisories.
* Test the application after upgrading dependencies.