# Domain Driven Design - Notes (Not the Eric Evans book, This is general)

* To avoid [inappropriate intimacy code smell](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy), if two microservices need to collaborate a lot with each other they should probably be the same microservice.
* Persistence Ignorance - The principle of Persistence Ignorance (PI) holds that classes modeling the business domain in a software application should not be impacted by how they might be persisted. Persistence tasks should be performed by the infrastructure layer.