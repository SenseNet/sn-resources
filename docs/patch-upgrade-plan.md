# Patch (update) plan for SNaaS

## Required releases (packages)
 - sensenet (core) services (check another backend repositories for changes and add the related releases if necessary)
 - sn-identityserver (check possible template changes)
 - snaas-services
 - sn-client
 - snaas-profile

## Update flow for individual repositories
1. sensenet core (and additional other backend) packages
2. sn-repobase (from snaas-services)
3. sn-identity server (templates)
4. restart

## Update on common SNaaS environments (after updating the customer repositories)
1. Update snover (sensenet core + snaas-services -> snover-netcore)
2. Update central IS
3. Update admin-ui
4. Update SNaaS profile
5. Update sensenet.com
