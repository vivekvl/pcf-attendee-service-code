#!/bin/bash

set -xe

pwd
env

cf api $PWS_API --skip-ssl-validation

cf login -u $PWS_USER -p $PWS_PWD -o "$PWS_ORG" -s "$PWS_SPACE"

cf routes

echo "Routing new deployment to public"

set +e
cf unmap-route attendee-service app.dev.digifabricpcf.com -n attendee-service-public
cf map-route attendee-service-green app.dev.digifabricpcf.com -n attendee-service-public
#cf delete attendee-service -f -r #revisit
cf rename attendee-service attendee-service-blue  #revisit
cf rename attendee-service-green attendee-service  #revisit
set -e

echo "Routes updated"

cf routes
