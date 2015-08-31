# Domain-driven JavaScript

[Domain-driven design](http://en.wikipedia.org/wiki/Domain-driven_design) for JavaScript and Node.js.

Apply Domain-driven Design to the Core Domain. That part of the business Domain that is of primary importance to the success of the organisation.

## Ubiquitous Language

Shared language within a single Bounded Context.

Used to drive the design of the Domain Model and API.

## Bounded Contexts

Provides a boundary around an application or system within which a Domain Model exists. Constraining a Ubiquitous Language such that terms and phrases have a specific meaning within it.

**Example:** A `Product` in an e-commerce application may have a different meaning in a catalog context, an inventory context and an invoicing context.

## Context Maps

# Tactical Modeling

Applied within a Bounded Context, using DDD’s building block patterns.

## Entities

Are distinguishable from each other due to their unique identity. Rather than their attributes.

Can be continuously changed over a long period of time.

## Value Objects

## Aggregates

An Aggregate is composed of either a single Entity or a cluster of Entities and Value Objects that must remain transactionally consistent throughout the Aggregate’s lifetime.

Instances are persisted using a Repository.

Publish Domain Events.

## Domain Services

Domain logic, domain-specific operations and process that doesn't naturally fit within Aggregates, Entities or Value Objects should be grouped within a Domain Service. 

Domain Services are stateless.

Publish Domain Events to indicate the occurrence of significant happenings in the domain. To notify external parties to changes that have occured.

## Domain Events

Inform something that has already happened.

Must be in the past tense and cannot fail.

May be used to notify external Bounded Contexts, or provide notifications for integration with interested third parties. 

Allow an Event-Driven Architecture and eventual consistency between Aggregates and/or Bounded Contexts.

## Application Services

Application Services are the direct clients of the domain model. Responsible for task coordination of use case flows, security, authorisation and transactions. 

No domain business logic should exist in Application Services. Instead, push them into the domain model; within Aggregates, Value Objects or Domain Services.

Provide the API through which external consumers may use the core domain. Application Services may expose functionality through functions accepting primitive types, or possibly DTOs. Alternatively, and preferrably, they will accept Command objects.

## Infrastructure Services

Used to abstract technical concerns (e.g. MSMQ, email provider, etc).

## Commands

> Encapsulate a command request as an object. Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.

Commands capture the user's intent. 

They are named in the imperative: create account; upgrade customer; complete checkout.

A command can fail, or be declined.

Command instances may be passed to an Application Service method. Or published onto a message queue to be dispatched to a Command Handler. These handlers are semantically equivalent to an Application Service method.

## Infrastructure
### Repositories
### Event Publishing

## Architecture
### Hexagonal (Ports and Adapters)

Input and output ports to facilitate communication with the core Domain Model. 

Adapters are created for each I/O port and consumer. Siting between clients, on the outside, and the core, on the inside.

Inputs: HTTP (REST, SOAP), message queue (AMQP)
Outputs: persistence, messaging

### Command-Query Responsibility Segregation (CQRS)

Separate write operations (commands) from reads (queries).