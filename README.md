# Backbase Training Exercises

## Portal Backend - Module 2: Content Services

In this module, we will see how to communicate with Content Services application using CMIS client and how to extend default functionality with custom validation rules.

You will create Camel-based integration route in CXP Portal application and configure it to communicate directly with Content Services. You'll also create a custom validator to control format of stored data.

### Prerequisites

All exercises use the [standard portal set-up for Backbase training](https://my.backbase.com/resources/how-to-guides/getting-your-first-launchpad-based-portal-set-up/).

### Contents

This module contains two components:

1. camel-cmis-uploader : Camel based integration route to automatically upload files from the file system to Content Services repository using Java CMIS client. For details check 
[camel-cmis-uploader](camel-cmis-uploader).

2. contentservices-validator : Content Services extension code which validates repository content to match defined data format. For details check
[contentservices-validator](contentservices-validator).
