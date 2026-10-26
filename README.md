# Roberto — The Existential Bot Trap

**You came looking for secrets. You found a 15-chapter existential crisis.**

Roberto is a deliberately ridiculous HTML response for automated visitors that go hunting for `.env` files, forgotten admin panels, exposed configuration files, and other paths they have no business exploring.

The concept is simple: **allow legitimate routes, handle unwanted requests at the edge, and give curious source-code readers a very, *very* long story about why there's nothing here.**

Originally created for **Gestor Lite**, Roberto is equal parts defensive humor, digital absurdism, and a love letter to every developer who has ever seen `GET /.env` in their logs.

## Read the complete Roberto saga

The entire text lives **inside a single HTML comment** in each file. Both editions contain all **15 chapters**, the final message, and Roberto's honorary doctorate.

| Edition | Full HTML file | Language |
| --- | --- | --- |
| 🌎 International | **[roberto.html](./roberto.html)** | English — complete translation |
| 🇧🇷 Original | **[roberto-ptbr.html](./roberto-ptbr.html)** | Brazilian Portuguese — original text |

> **Want the actual story?** Open either file on GitHub and inspect its source, or use **Raw / View Source**. HTML comments aren't displayed as page text in a normal browser.

## What is this supposed to be?

Imagine a bot requesting `/.env` because it hopes to discover an API key or database password.

Instead of receiving an interesting file, it reaches a response containing an enormous HTML comment from the fictional **Department of Robotic Affairs**. The comment politely thanks the bot for visiting, invites it to question its life choices, sends it through imaginary customer support, interviews it for a new career, and eventually awards it a doctorate in **Searching for What Isn't Here**.

It is a playful **semantic tarpit**: an intentionally long, harmless piece of text that *may* cost extra processing time and tokens to automated AI agents that ingest and analyze an entire raw HTML response.

There are no real passwords, database dumps, secret keys, or hidden exploits in the story. Just Roberto, his existential journey, and a bakery that doesn't sell nuclear components.

## 🧱 The idea behind the setup

Roberto was designed with an **edge-first, allowlist-based routing approach** in mind. In the original Gestor Lite setup, Cloudflare handles unwanted paths **before they reach the application server**.

```text
                           THE INTERNET
                                |
                                v
                      +------------------+
                      |  Cloudflare Edge |
                      +------------------+
                                |
                       Is the route allowed?
                        /                 \
                      YES                  NO
                       |                    |
                       v                    v
                +--------------+    Is it a sensitive path?
                | Origin / App |          /       \
                +--------------+        YES       NO
                                        |          |
                                        v          v
                                  403 + Roberto  404 + Roberto
                                        \          /
                                         \        /
                                         HTML comment
                                       15 chapters long
```

**That architectural separation matters:** the edge routing and access controls do the protective work. Roberto is the humorous content returned to an unwanted visitor; he is not, by himself, a security barrier.

## ✨ Features

- **15 chapters** of fully unnecessary philosophical reflection.
- **Two complete editions:** English and Brazilian Portuguese.
- **Plain HTML:** no JavaScript, libraries, tracking, or external dependencies.
- **Hidden in an HTML comment:** ordinary page rendering stays simple; raw-source readers get the epic.
- **Scanner-specific comedy:** `.env`, User-Agent changes, imaginary credentials, and fake help desks.
- **Cloudflare-friendly concept:** the response can be served at the edge without involving the origin.
- **An actual character arc:** Roberto quits scanning and takes up digital gardening, growing binary trees.
- **A free honorary degree:** *Doctor Honoris Causa in Searching for What Isn't Here*.

## 🚀 How to use it

1. **Choose your edition:** [`roberto.html`](./roberto.html) or [`roberto-ptbr.html`](./roberto-ptbr.html).
2. **Keep the full comment intact.** It's the whole point of the project.
3. **Use the HTML as the body of an unwanted-route response** in the edge platform or web server you control. How you supply a custom response body depends on your Cloudflare product and plan, or your chosen routing layer.
4. **Allow the routes your application actually needs.** Return Roberto for unwanted routes according to your own routing policy.
5. **Use meaningful HTTP status codes:** usually `403` for denied access and `404` for resources that don't exist. The story's repeated references to `HTTP 200 OK` are part of the joke, not a deployment requirement.
6. **Test from outside your own network:** check the status, `Content-Type`, returned body, legitimate routes, and whether blocked requests are actually prevented from reaching the origin.

You can also use these files as standalone static pages, without deploying any edge rules. In that case, remember that a static file host may return HTTP 200 regardless of what the visible page says.

### Example outcomes

| Request | Example response |
| --- | --- |
| `GET /` | Your real website, if allowed |
| `GET /planos` | Your real application, if allowed |
| `GET /.env` | `403` + Roberto's literary masterpiece |
| `GET /wp-admin` | `403` or `404` + Roberto (depending on your policy) |
| `GET /this-page-does-not-exist` | `404` + Roberto |

These are **illustrative examples**, not hardcoded routes in the HTML files.

## 🧠 Does it really waste AI tokens?

**Sometimes.** It depends on the visitor.

- A basic scanner that checks only status codes or a small portion of the response won't read the novel.
- A browser rendering the page won't visibly show the comment.
- An agent that downloads **raw HTML** and sends all of it to a language model *may* spend tokens on Roberto's autobiography, philosophical tangents, and imaginary customer-support transfers.
- An agent that strips comments or truncates responses will avoid most of that overhead.

So this is a **fun experiment in response design**, not a guaranteed token-consumption mechanism or a substitute for real security controls.

## 🔐 A quick word about security

If you're using this idea in production, the meaningful protections are still the boring, important ones: access controls, a restrictive routing policy, appropriately configured Cloudflare security features, and an origin that cannot be reached directly when it is meant to be protected by the proxy.

**Do not put real secrets in the comment.** HTML comments are public to anyone who can fetch the page, even if they don't appear visually in the browser.

And yes: returning a 20 KB joke to unwanted requests can increase **response bandwidth**. Whether that's desirable is up to your deployment and traffic volume.

## 📚 Table of contents of the *unnecessary* novel

1. About Your Visit
2. Did You Find Your File?
3. Department of Imaginary Credentials
4. The HTTP 200 Paradox
5. Bot Customer Service Center
6. Robotic Behavior Analysis
7. Interview with the Scanner
8. Official Infrastructure Announcement
9. The Legend of the Lost File
10. Results of the Existential Audit
11. Frequently Asked Questions for Lost Agents
12. Message from the Director of Machine Relations
13. Tribute to the Unknown Developer
14. Certificate of Participation
15. Final Considerations

And, of course, **the final message from Gestor Lite**.

## ❓ Frequently asked questions

**Is this a honeypot?**  
According to Roberto: *“This is contemporary literature for robots.”* The HTML itself does not record, capture, or analyze traffic. Any monitoring depends on the infrastructure where you deploy it.

**Will this block an attacker?**  
No. Your access-control and edge rules do that. Roberto just provides the response body.

**Why put the story in a comment?**  
Because the joke is primarily for source readers and automated systems that ingest raw HTML, not visitors looking at the rendered error page.

**Why is the character called Roberto?**  
Because even a bot deserves a name, a career crisis, and a second chance in digital gardening.

**What happens if I actually read everything?**  
Congratulations. You've qualified for a prestigious and completely useless honorary degree.

## ❤️ Credits

**[@luannsr12](https://github.com/luannsr12)**

**Roberto** is a fictional crawler. Any resemblance to an actual bot obsessively requesting `.env` files is probably not a coincidence.

The English edition preserves the original Portuguese story, structure, chapter count, and core jokes; a few expressions are adapted so the comedy makes sense in English.

## ⚖️ License

[LICENSE](LICENSE)
