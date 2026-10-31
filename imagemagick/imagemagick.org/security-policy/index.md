# ImageMagick | Security Policy

v7.1.2-34 Latest Stable Release

# Security Policy

Learn how to configure and enforce ImageMagick’s security policy to balance functionality with protection. Explore open, limited, secure, and websafe options, along with resource limits, coder restrictions, and best practices for securing containers, servers, and web applications.

   Get ImageMagick    Documentation

 quickstart.sh

# Install via your favorite Package Manager

$ brew install imagemagick

# Convert PNG to WebP with compression

$ magick input.png -quality 85 output.webp

# Resize image maintaining aspect ratio

$ magick input.jpg -resize 800x600^ output.jpg

 Security Policy • Environment Selection • Example Policy • Discussion • Pixel Cache Sync • Zero Config • Best Practices

#### ImageMagick Security Policy

Establish a security policy tailored to your environment before deploying ImageMagick. ImageMagick operates on an "everything allowed unless denied" model, where the last matching policy wins. Place broad deny rules first, followed by specific exceptions, and review rule ordering carefully to prevent unintended authorizations.

ImageMagick is intentionally open by default, a design choice optimized for controlled, sandboxed environments like Docker containers and isolated application pipelines.

Security involves balancing protection against potential vulnerabilities with practical operational needs. ImageMagick's security policy acts as the control point between strict lockdown and convenience, letting you dictate which features, coders, and operations are permitted.

### A well-designed policy empowers you to:

- Limit or disable high-risk coders and external operations to minimize attack surfaces.

- Constrain resource usage to prevent denial-of-service (DoS) attacks and resource exhaustion.

- Define strict input boundaries for what file types and formats ImageMagick may process.

- Tailor defenses to your specific threat model rather than relying on a rigid, one-size-fits-all setup.

Because ImageMagick ships in an open state for easy integration into containers and automated build pipelines, administrators must tighten policies to match production requirements. The more untrusted input your application handles, the more restrictive your policy must be.

Policies are evaluated using a "last matching policy wins" model. For filesystem paths, ImageMagick evaluates canonical (fully resolved) paths and enforces canonical denies to block bypass attempts via symlinks, alternate representations, or path traversal tricks.

## Selecting the Right Security Policy for Your Environment

To ensure optimal security in public-facing applications, you can restrict ImageMagick exclusively to web-safe formats like GIF, JPEG, and PNG. Alternatively, you can customize limits for memory allocation, allowed read/write paths, sequence frame counts, workflow runtime, and pixel cache disk space.

Setting resource limits protects against malicious or malformed files—such as an internet-sourced image crafted to declare 20,000×20,000 dimensions. Without limits, such files can exhaust memory and disk space, causing system slowdowns or crashes. You can configure these limits in your policy.xml file.

Environments vary wildly: a sandboxed internal service with abundant RAM has different security needs than a public web server processing user uploads. To simplify hardening, ImageMagick provides four pre-built security policies (available as of version 7.1.1-16):

##### open

The default profile. Ideal for secure, firewalled environments or Docker containers where broad functionality and convenience are prioritized over strict lockdown.

##### limited

Strikes a balance between usability and security. Disables hazardous coders (like SVG or HTTP) and applies adjustable resource constraints on memory, storage, and runtime.

##### secure

A rigorous profile enforcing strict resource caps, explicit read/write pathways, sequence limits, and disabled high-risk capabilities for hardened deployments.

##### websafe

Designed for public websites. Restricts I/O strictly to GIF, JPEG, and PNG formats while blocking image filters and indirect reads to prevent exploitation.

Under Linux, select your policy using the configure script option --with-security-policy={open,limited,secure,websafe}. Under Windows, select it during the GUI configuration app workflow.

We encourage reviewing every rule in your policy.xml. Finding the right balance ensures robust defense without breaking legitimate image processing pipelines.

Policy Evaluator: Doyensec provides a helpful interactive security policy auditor at imagemagick-secevaluator.doyensec.com.

## Example Hardened Security Policy

Below is a production-ready example of a hardened security policy tailored for public-facing web applications:

 policy.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policymap [
  <!ELEMENT policymap (policy)*>
  <!ATTLIST policymap
    xmlns CDATA #FIXED ""
  >
  <!ELEMENT policy EMPTY>
  <!ATTLIST policy
    xmlns   CDATA   #FIXED ""
    domain  NMTOKEN #REQUIRED
    name    NMTOKEN #IMPLIED
    pattern CDATA   #IMPLIED
    rights  NMTOKEN #IMPLIED
    stealth NMTOKEN #IMPLIED
    value   CDATA   #IMPLIED
  >
]>
<policymap>
  <!-- Resource Limits -->
  <policy domain="resource" name="thread" value="4"/>
  <policy domain="resource" name="time" value="60"/>
  <policy domain="resource" name="file" value="768"/>
  <policy domain="resource" name="memory" value="256MiB"/>
  <policy domain="resource" name="map" value="512MiB"/>
  <policy domain="resource" name="area" value="32MP"/>
  <policy domain="resource" name="disk" value="1GiB"/>
  <policy domain="resource" name="list-length" value="16"/>
  <policy domain="resource" name="width" value="4KP"/>
  <policy domain="resource" name="height" value="4KP"/>
  <policy domain="resource" name="throttle" value="2"/>
  <policy domain="resource" name="dynamic-throttle" value="false"/>
  <!-- Pixel Cache Security -->
  <policy domain="cache" name="memory-map" value="anonymous"/>
  <policy domain="cache" name="synchronize" value="true"/>
  <!-- Delegate and Filter Restrictions -->
  <policy domain="delegate" rights="none" pattern="*"/>
  <policy domain="filter" rights="none" pattern="*"/>
  <!-- Path Restrictions -->
  <policy domain="path" rights="none" pattern="-"/>
  <policy domain="path" rights="none" pattern="[Ff][Dd]:*"/>
  <policy domain="path" rights="none" pattern="/etc/*"/>
  <policy domain="path" rights="none" pattern="*../*"/>
  <policy domain="path" rights="none" pattern="@*"/>
  <policy domain="path" rights="none" pattern="|*"/>
  <!-- Module Restrictions -->
  <policy domain="module" rights="none" pattern="*"/>
  <policy domain="module" rights="read | write" pattern="{GIF,JPEG,PNG,WEBP}"/>
  <!-- System Security Options -->
  <policy domain="system" name="shred" value="1"/>
  <policy domain="system" name="memory-map" value="anonymous"/>
  <policy domain="system" name="max-memory-request" value="256MiB"/>
  <policy domain="system" name="max-profile-size" value="16MiB"/>
  <policy domain="system" name="max-profile-count" value="16"/>
  <policy domain="system" name="symlink" rights="none" pattern="follow"/>
  <policy domain="system" name="svg" rights="none" pattern="substitute-entities"/>
</policymap>
```

## Security Policy Discussion & Advanced Tuning

Starting with ImageMagick 7.0.1-8, external delegates can be globally disabled by setting the pattern to "*". Glob patterns are case-sensitive prior to version 7.1.1-16, so coders must be uppercase (e.g., "EPS") or use case-insensitive patterns like [Pp][Nn][Gg].

When restricting coders like HTTPS, attempting an unauthorized operation returns an error:

 $ magick https://imagemagick.org/image/wizard.png wizard.jpg
 magick: attempt to perform an operation not allowed by the security policy `HTTPS'
 magick: no images defined `wizard.jpg'

You can also use anonymous memory mapping and buffer shredding to enhance data hygiene:

 <policy domain="system" name="memory-map" value="anonymous"/>
 <policy domain="cache" name="memory-map" value="anonymous"/>
 <policy domain="system" name="shred" value="1"/>

To verify your active security policy configuration at any time, run:

 $ magick identify -list policy

## Pixel Cache Synchronize Policy

When writing pixels to disk, ImageMagick preallocates and memory-maps files for performance. However, if disk space runs out during population, the OS may trigger a SIGBUS signal. Setting synchronize to true ensures data is flushed and synchronized immediately, preventing crashes and offering early error reporting:

 <policy domain="cache" name="synchronize" value="true"/>

## Zero Configuration Security Policy

For embedded builds that prohibit external configuration files, you can embed policies directly into the source module MagickCore/policy-private.h before compilation:

 static const char *ZeroConfigurationPolicy = \
 "<policymap> <policy domain=\"module\" rights=\"none\" pattern=\"MVG\"/> </policymap>";

## Other Security Best Practices

- Use web-safe image formats: Restrict processing strictly to trusted formats like GIF, JPEG, and PNG.

- Customize resource limits: Control memory, disk space, and runtime bounds to thwart denial-of-service attacks.

- Deploy sandboxing: Run ImageMagick inside isolated containers or restricted user namespaces.

- Disable dangerous coders: Turn off vector graphics (MVG) and remote network fetches (HTTPS) on public instances.

- Review delegates: Audit delegates.xml and use absolute pathnames (e.g., /usr/bin/gs) to prevent path hijacking.

- Keep ImageMagick updated: Always run the latest stable release to incorporate critical security patches.
