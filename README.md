# infra-amazon-req

This module aims to ease the installation of a new infrastructure by giving the possibility to
* Create an S3 bucket for the remote state
* Create an infra user allowed to access such bucket
* Create code commit repository with both admin & read-only users

Each of those component are optional and can be disabled or enabled despite some dependencies.

# Job description

## Overview

**terraform-apply:**
Terraform job similar to the plan one, but will actually create/update everything that needs to. Please see the plan diff for a better understanding.
Please see 'Consideration' on why there isn't any 'plan' job on this stack.

## /!\ Destroy /!\

**terraform-destroy:**
Terraform job meant to destroy the whole stack - **NO CONFIRMATION ASKED**. If triggered, the full project **WILL** be destroyed.

Use with caution.

# Consideration

## Creation

Because of the very own nature of this stack (likely first one to run), there are some elements to keep in mind. There is no 'plan' via terraform as it couldn't store the planned tfstate into s3 bucket, as it wouldn't exist quite yet. Which is why it only disposes of an 'apply' terraform job instead of both.

## Destruction

By default the stack will fully delete everything, that includes the S3 bucket in which the remote state is stored. You can disable it by setting the 'force_destroy' to false; but it's likely to make the overall destruction job fail - as the bucket wouldn't empty.
