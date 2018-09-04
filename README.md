# infra-amazon-req

This module aims to ease the installation of a new infrastructure by giving the possibility to
* Create an S3 bucket for the remote state
* Create an infra user allowed to access such bucket
* Create code commit repository with both admin & read-only users

Each of those component are optional and can be disabled or enabled despite some dependencies.
