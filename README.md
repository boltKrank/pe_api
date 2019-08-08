# pe_api
API curl examples for Puppet enterprise

# Use cases:

## Configuration drift:

[Configuration drift](./configuration.md)

## Conpliance (CIS):

[Compliance](./copliance.md)

## Vulnerability remediation via tasks:

[Running tasks](./tasks.md)

## Status of nodes under management:

## TODO:

c.       Integration with ServiceNow:
 i.      Puppet to provide API for ServiceNow to query/obtain:
-          Status of all nodes under management.
o   Datetime.
o   Each node up and running?
o   Configuration drift detected (with datetime of detection).
-          Detected non-compliances in nodes under management.
o   Datetime.
o   Node name/IP.
o   Configuration drift details.
o   Action taken by Puppet (with datetime).
                                                             ii.      Puppet to provide API for ServiceNow to trigger threat/vulnerability remediation tasks.
ServiceNow request to specify:
-          node name/IP.
-          CVE number of detected threat/vulnerability.
Is there a way to let ServiceNow know the triggered remediation tasks are:
-          Completed successfully with details.
-          Failed with details.



# Puppet enterprise APIs:

## RBAC service API v1
- Managing access to Puppet Enterprise.
- Connecting to external directories.
- Generating authentication tokens.
- Managing users, user roles, user groups, and user permissions.

## RBAC service API v2
- Revoking authentication tokens.

## Node classifier service API
- Querying the groups that a node matches.
- Querying the classes, parameters, and variables that have been assigned to a node or group.
- Querying the environment that a node is in.

## Orchestrator API
- Gathering details about the orchestrator jobs you run.
- Inspecting applications and applications instances in your Puppet environments.

## Code Manager API
- Creating a webhook to trigger Code Manager.
- Queueing Puppet code deployments.
- Checking Code Manager and file sync status.

## Status API
- Checking the health status of PE services.

## Activity service API
- Querying PE service and user events logged by the activity service.

## Razor API
- Provisioning bare-metal machines.


# Puppet open-source APIs:

## Puppet Server administrative API endpoints

`environment-cache`

`jruby-pool`

- Deleting environment caches created by a Puppet master.
- Deleting the Puppet Server pool of JRuby instances.

## Server-specific Puppet API
- Environment classes
- Environment modules
- Static file content

Getting the classes and parameter information that is associated with an environment, with cache support.

Getting information about what modules are installed in an environment.

Getting the contents of a specific version of a file in a specific environment.

## Puppet Server status API 	
- Checking the state, memory usage, and uptime of the services running on Puppet Server.

## Puppet Server metrics API
- v1 metrics (deprecated)
- v2 metrics (Jolokia)

Querying Puppet Server performance and usage metrics.

## Puppet HTTP API
- Retrieving a catalog for a node
- Accessing environment information
- For information on how this API is used internally by Puppet, see Agent/Master HTTPs Communications page

## Certificate Authority (CA) API
- Used internally by Puppet to manage agent certificates.
- See Agent/Master HTTPs Communications for details. See Puppet's Commands page for information about the Puppet Cert command line tool.

## PuppetDB APIs
- Querying the data that PuppetDB collects from Puppet
- Importing and exporting PuppetDB archives
- Changing the PuppetDB model of a population
- Querying information about the PuppetDB server
- Querying PuppetDB metrics

## Forge API
- Finding information about modules and users on the Forge
- Writing scripts and tools that interact with the Forge website
