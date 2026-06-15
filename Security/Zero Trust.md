Zero Trust is a security approach based on a the premise that no actor can be fully trusted (authentication) and verifications must be always made to ensure every actor is always who it claims to be (verification).

Access is granted only after we verify:

- Who is requesting the access 
- What device are they using
- What's their location (IP) and behavior (assumed roles)
- What's their risk level

Verification doesn’t happen only once. It's continuous, ensuring that trust is maintained throughout a session.

## Zero Trust principles

Zero Trust is built on three principles that govern access decisions and security controls.

| **Principle**                  | **Implementation**                                                                                                                                                                                            |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Verify explicitly**          | Every access request is **authenticated and authorized using all available signals**.                                                                                                                         |
| **Use least privilege access** | User and workloads get **only the access they need, for the shortest time required**.                                                                                                                         |
| **Assume breach**              | Security controls are designed with the expectation that **attackers might be operating inside the environment**. Controls focus on limiting breach impact, and enabling rapid threat detection and response. |