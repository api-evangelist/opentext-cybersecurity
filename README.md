# OpenText Cybersecurity

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

OpenText Cybersecurity is the security business of OpenText, assembled from the Micro Focus security
portfolio (Fortify, ArcSight, NetIQ, Voltage) and the SMB/MSP brands acquired through Webroot, Carbonite
and Zix.

## What this profile found

Two of the product lines expose a public developer surface, and both are captured here.

| Surface | What is published | Where |
|---|---|---|
| OpenText Core Application Security (Fortify on Demand) | Swagger 2.0, 159 operations over 125 paths, 238 definitions. Served live and unauthenticated from `api.ams` / `api.emea` / `api.apac.fortify.com`. 100% operationId and summary coverage. | `openapi/` |
| SAST Aviator | Six first-party proto3 service definitions, 6 gRPC services, 20 RPCs | `grpc/` |
| Webroot Unity API | Public HTML API reference, OAuth 2.0 with a nine-scope vocabulary, a documented seven-event notification catalogue with fetch and webhook delivery, and a dated service-build change history | `asyncapi/`, `scopes/`, `changelog/` |
| Agent surfaces | A provider-published `llms.txt`, a provider-published Agent Skills package (nine skills, two agents, four assistant runtimes), and a first-party MCP server shipped inside the Fortify CLI | `llms/`, `skills/`, `mcp/`, `cli/` |

## Gaps worth a provider conversation

- **No `/.well-known/security.txt` on any of ten hosts**, at a company that sells vulnerability management. Eighty well-known probes returned zero documents.
- **No idempotency mechanism** across 71 mutating Fortify on Demand operations. Re-firing a scan start after a timeout can consume a second entitlement.
- **No published rate limit.** HTTP 429 is declared on 143 of 159 operations, with no number, no window and no `Retry-After` or `RateLimit-*` header.
- **No `securityDefinitions` in the contract.** The OAuth scopes are real and published — one per operation, in free text inside each operation's own description — so a generated client gets no auth layer at all.
- **No AsyncAPI** for the Webroot Unity event surface, and no published payload schema for any of its seven event types.
- **Compliance evidence is behind a bot wall.** Every `www.opentext.com` URL returns HTTP 444 to non-browser clients. The FedRAMP authorization was verifiable only because the US government publishes it.

