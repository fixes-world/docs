---
description: Welcome to 𝔉rc20 Developer Service documentation
---

# Open API Service

{% hint style="info" %}
<mark style="color:green;">Please read</mark> [FIXeS Open API Service Legal Disclaimer](legal-disclaimer.md) <mark style="color:green;">before using FIXeS Open API Service.</mark>
{% endhint %}

## Overview

FIXeS Open API Service is open to community developers, allowing you to explore the world of FIXeS executable inscription. You can deploy your own inscribing services, bulid wallet applications, develop browsers, and much more using this API.

## Getting an API Key

To use the FIXeS Open API Service, please request an `API_KEY` from us by sending an email to [fixesonflow@gmail.com](mailto:fixesonflow@gmail.com) with the name and description of your project and the reason for using it. After we review it, we will send you the `API_KEY`.

When you obtain the API key, please add it to the request header with the `Authorization` format as follows:

```bash
curl --location 'http://open-api.fixes.world/v1/utils/flow-price' \
--header 'Authorization: Bearer YOUR_API_KEY'
```

