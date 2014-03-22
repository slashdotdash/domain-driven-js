# Domain-driven JavaScript

[Domain-driven design](http://en.wikipedia.org/wiki/Domain-driven_design) for JavaScript and Node.js.

## Ubiquitous Language

## Bounded Contexts

## Entities

## Aggregates

## Value Objects

## Domain Events

Inform something that has already happened.

Must be in the past tense and cannot fail,

May be used to notify external Bounded Contexts, or provide notifications for integration with interested third parties. 

## Application Services

Application Services are the direct clients of the domain model. Responsible for task coordination of use case flows, security, authorisation and transactions.

No domain business logic should exist in Application Services. Instead, push them into the domain model. Within Aggregates, Value Objects or Domain Services.

Application Services may expose functionality through functions accepting primitive types, or possibly DTOs. Alternatively, and preferrably, they will accept Command objects.

## Domain Services

Domain logic and process that doesn't fit within Aggregates, Entities or Value Objects should be grouped within a Domain Service. 

Domain Services may publish Domain Events to notify external parties to changes that have occured.

## Commands

> Encapsulate a command request as an object. Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.

Commands capture the user's intent. 

They are named in the imperative: create account; upgrade customer; complete checkout.

A command can fail, or be declined.


## Infrastructure
### Repositories
### Event Publishing