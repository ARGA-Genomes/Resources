# Running specieslist-webapp via Docker

- Specieslists-webapp repo: https://github.com/AtlasOfLivingAustralia/specieslist-webapp \
  Grails webapp that uses MySQL DB
- BioAtlas docker repo: https://github.com/bioatlas/ala-docker \
  Swedish BioAtlas run all of the ALA apps/services via Docker, so this is a good model to follow

The idea is to run up an instance of specieslist-webapp in a Docker container via docker-compose,
similar to how the [Pipelines processing](https://github.com/gbif/pipelines/tree/dev/livingatlas) uses docker-compose for SOLR, SDS and name-matching-index services.

This code is incomplete and not yet functional but this should be a good start on getting it working.

## Still TODO:

- [ ] manage secrets (DB creds, api keys)
- [ ] push specieslist-webapp image to [ALA Dockerhub org](https://hub.docker.com/orgs/atlasoflivingaustralia/repositories) and then reference this image in docker-compose file
- [ ] get MySQL database working
- [ ] get specieslist-webapp port and URL configured correctly
- [ ] specieslist-webapp version is hardcoded in dockerfile - needs to be config driven
