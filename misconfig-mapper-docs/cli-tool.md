# CLI Tool

## CLI Tool

**Misconfig Mapper** has a [dedicated open-source CLI tool](https://github.com/intigriti/misconfig-mapper) written in Golang to help you automate the testing of most misconfigurations found on covered services.\
\
It can identify and enumerate instances of services used by your company, and perform detection and misconfiguration checks at scale! By supplying a template with detection fingerprints and misconfiguration check fingerprints, the tool can quickly and accurately identify potential security risks in popular third-party software and services!\
\
The tool is based on templates and is versatile. New services can be easily added by adding them to the `services.json` file.

### Features

* The CLI tool is based on templates defined in the `services.json` file. You can add as many as you want. See [_Templates section_](cli-tool.md#templates) for more information on how to add a template.
* If you provide a company name, the tool will automatically generate permutations based on the keyword you provided and try to find any matching services.
* You can also optionally select to only detect the presence of services without performing any misconfiguration checks (see more on [_Usage section_](cli-tool.md#usage)).

## Installation

To install Misconfig Mapper, you can clone the repository and compile the code from source or [download the latest release](https://github.com/intigriti/misconfig-mapper/releases).

{% hint style="success" %}
If you decide to download a release, make sure to run the following command to install the required templates: \
```
./misconfig-mapper -update-templates
```
This command will ensure that you download the latest templates that misconfig-mapper requires. \
{% endhint %}

#### From source

If you want to build your own instance from source, ensure you have the latest version of Golang installed. To verify your installation, run:

```bash
$ go version
  go version go1.21.5 linux/amd64
```

1. Clone this repository:

```bash
$ git clone https://github.com/intigriti/misconfig-mapper.git
```

2. Next, compile your binary from source:

```bash
$ go build -o misconfig-mapper
```

3. Finally, add or move the binary to a folder in your `$PATH` (optional)

### Usage

**Example 1:** Perform a scan to enumerate all misconfigured third-party services

```basic
$ ./misconfig-mapper -target "yourcompanyname" -service 1 -delay 1000
```

![Example 1](../.gitbook/assets/cli-tool/0.png)

**Example 2:** Perform a detection-only scan to enumerate all third-party services (without checking for any misconfigurations)

```bash
$ ./misconfig-mapper -target "yourcompanyname" -service 1 -skip-misconfiguration-checks true
```

![Example 2](../.gitbook/assets/cli-tool/1.png)

**Example 3:** Only test for one specific service (by ID or name)

```bash
$ ./misconfig-mapper -target "yourcompanyname" -service 1
```

```bash
$ ./misconfig-mapper -target "yourcompanyname" -service "drupal"
```

![Example 3](../.gitbook/assets/cli-tool/2.png)

**Example 4:** Print out all loaded services

```bash
$ ./misconfig-mapper -list-services
```

<figure><img src="../.gitbook/assets/cli-tool/3.png" alt=""><figcaption><p>Example 4</p></figcaption></figure>

Additionally, you can pass request headers using the `-headers` flag to comply with any request requirements (separate each header using a **double semi-colon**):

```
-headers "User-Agent: xyz;; Cookie: session=eyJ...;;"
```

```
Usage of ./misconfig-mapper:
  -delay int
    	Specify a delay between each request sent in milliseconds to enforce a rate limit.
  -headers string
    	Specify request headers to send with requests (separate each header with a double semi-colon: "User-Agent: xyz;; Cookie: xyz...;;")
  -list-services
    	Print all services with their associated IDs
  -max-redirects int
    	Specify the max amount of redirects to follow. (default 5)
  -permutations string
    	Enable permutations and look for several other keywords of your target. (default "true")
  -service string
    	Specify the service ID you'd like to check for: "0" for Atlassian Jira Open Signups. Wildcards are also accepted to check for all services. (default "0")
  -skip-misconfiguration-checks string
    	Only check for existing instances (and skip checks for potential security misconfigurations).
  -target string
    	Specify your target domain name or company/organization name: "intigriti.com" or "intigriti" (files are also accepted)
  -timeout int
    	Specify a timeout for each request sent in milliseconds. (default 7000)
  -update-templates
    	Pull the latest templates & update your current services.json file
  -verbose
    	Print verbose messages
```

### Templates

You can easily define more templates to scan for. Templates are in a structured JSON object and read from `services.json`\
\
To define more services, edit the services.json file and separate each misconfiguration in your `services.json` file.

An example template definition schema is available [here](https://github.com/intigriti/misconfig-mapper/#templates).

{% hint style="success" %}
To update the service.json file to the latest version, simply run:\
```
./misconfig-mapper -update-templates
```
This command will pull the latest templates from Github.\
{% endhint %}

#### Template Type Definitions

**ID**

**Type:** number\
\
The `id` field is used to identify the service when the `-service` flag is provided. It should be a numerical value that follows the sequence of previous IDs.

#### Request

**Method**

**Type:** string

The `method` field is used to provide a HTTP method.

**BaseURL**

**Type:** string

The `baseURL` field is used to locate the third-party service, if it exists.

{% hint style="success" %}
The CLI tool can auto-detect and replace the **"{TARGET}"** template variable with the target provided using the target flag.\
\
Example: https://{TARGET}.example.com will allow the tool to look for:

* https://yourcompanyname.example.com
* https://yourcompanyname-app.example.com
* https://yourcompanyname-eu.example.com
* ...
{% endhint %}

**Path**

**Type:** string

The `path` field checks whether the service is vulnerable by observing the response.

{% hint style="success" %}
The CLI tool can auto-detect and replace the **"{TARGET}"** template variable with the target provided using the target flag.\
\
Example: /app/{TARGET} will allow the tool to look for:

* https://example.com/app/yourcompanyname
* https://example.com/app/yourcompanyname-app
* https://example.com/app/yourcompanyname-eu
* ...
{% endhint %}

**Headers**

**Type:** object array

The `headers` field is used to supply any required request headers.

**Body**

**Type:** string | null

The `body` field is used to supply a raw request body.

{% hint style="info" %}
Set the request body to **null** if there's no need to send a request body.
{% endhint %}

#### Response

**StatusCode**

**Type:** int

The `statusCode` field is used to validate the matching response status code and further minimize the chances of false positive results.

**Detection Fingerprints**

**Type:** string array

The `detectionFingerprints` field supports enumeration & validation of a third-party service for your target. These fingerprints are used to mark the detection of a service or instance. Make sure to define strict regex patterns or keywords to minimize the chances of false positive results.

{% hint style="success" %}
Regex patterns are supported!
{% endhint %}

**Fingerprints**

**Type:** string array

The `fingerprints` field is used to validate the existence of a misconfigured third-party service for your target. Make sure to define strict regex patterns or keywords to minimize the chances of false positive results.

{% hint style="success" %}
Regex patterns are supported!
{% endhint %}

#### Metadata

**Service**

**Type:** string

The `service` field is used to display the service name in the CLI output results to visually confirm which service is currently being scanned.

**Description**

**Type:** string

The `description` field displays the service description in the CLI output once a service has been enumerated or identified and confirmed vulnerable.

**Reproduction Steps**

**Type:** string array

The `reproductionSteps` field reports back on how to reproduce the found misconfiguration. These steps are derived from this documentation.

{% hint style="info" %}
Each step should be in a separate array entry. You can specify as many steps as you'd like to.
{% endhint %}

**References**

**Type:** string array

The' references' field documents enumerated and misconfigured services. These references are derived from this documentation.

{% hint style="info" %}
Each reference should be in a separate array entry. You can specify as many references as you'd like to.
{% endhint %}
