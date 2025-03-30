# api

[GitHub Repository](https://github.com/HorseIncorporated/api)

`git clone git@github.com:HorseIncorporated/api`

https://www.postman.com/what-is-an-api/

- [ ] rename repo to service.api
- [ ] create a [POST] controller w/endpoint: /api/prompt 
	- [ ] controller should call service.auth
	- [ ] controller should call our configured service.prompt 


api is made to serve client requests

api should allow a user to authenticate (both locally and a deployed api service) with github

api should prompt the github user to accept the GitHub app into their life

api should allow a user to manage their configurations without exposing those values (via github app)

api can expose service components with the github user and their profile along with a request