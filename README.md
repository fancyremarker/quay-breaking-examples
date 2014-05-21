# quay-breaking-examples

Examples of Dockerfiles that break Quay.

## ~~passwordless-ssh~~

**FIXED.** (The issue was completely separate, and this example was trying to catch a red herring.)

    docker build -t quay.io/fancyremarker/passwordless-ssh passwordless-ssh
