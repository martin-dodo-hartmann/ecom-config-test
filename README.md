# ecom-config-test
Test repo for ecom configuration

Purpose of this repository is to be a sample on how an ecom appserver configuration could look like in the future.
We basically set two kinds of information here:
* Ecom appserver context configuration via properties file
* tomcat's java startup parameters

These are at first set on a global level and can be overwritten per realm or instance, if required.

The appserver-operator automatically grabs the latest configuration from this repo and applies it on new sandboxes. In 
addition he has a change listener and always applies the latest config to existing instances (which will trigger a 
restart automatically).

Like a normal upgrade, the appserver-operator does a canary-updade first to see, if the config is valid and if ecom
is healthy after updating.

**Note** that an update of the properties can happen at any time, but the restart must only take place within
the customer' maintenance window.

## Additional sources

In addition to these config repo we have two additional sources for configuration:
* license service -> for e.g. customer profiles (bronze, gold, etc)
* secret config provider (TBD) -> providing secret configuration (e.g. CloudFlare access keys)