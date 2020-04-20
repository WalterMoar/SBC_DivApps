# Redis HA

This highly available version of Redis is based heavily on the code from
https://github.com/openlab-red/redis-ha.

The following changes have been made:
1. Removed the `REDIS_SERVICE_PREFIX` from the deploymentconfigs.
1. Added default values for buildconfig and deploymentconfig parameters.
1. Automated PVC creation in master deploymentconfig.
1. Using four instances of the sentinels rather than five.
1. Using three instances of the replicas rather than five.
