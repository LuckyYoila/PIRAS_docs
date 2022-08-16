Software Architecture
======================

    This section outlines the technologies and paradigm used in the development of PIRAS.

    PIRAS was developed using the microservices architecture where the "backend" and "frontend" are loosely coupled, and communicate through APIs over HTTP(S).
    Below is a diagramatic representation of PIRAS' Architecture

.. figure:: /_static/images/architecture.png
   :alt: 'show the software achitecture'
   :align: center
   :width: 700

   *show the software achitectural design*


the outline below gives move infromation about the diagram above:

**User Access Layer:** this is the part of the platform accessed directly by users (e.g.Taxpayer), admins (e.g. MDAs), and third-party service providers: (e.g. OPAY). Apart from providing information via the browser; the user access level also provides JSON formatted information upon which Android, IOS, and desktop apps can be built.

**Views Layer:** This powers the user access layer and comprises an Angular JS
application for browsers, a *JSON* based service for native devices (e.g. Android), and *XML and JSON* for our third-party service providers. The system is written in Angular framework on the front end, CodeIgniter (PHP) on the backend.

**Security Layer:** All data that flow from the business logic layer to the views layer for user access must go through one, two, or all of the following authentication methods:
   * JWT: user supplies his password and TIN and is assigned an encrypted token which all further requests must come with to prove its the same user. This token expires after 15 minutes and must be re issued to remain valid.
   * Bearer Token plus IP whitelisting: this is for some of our third party service providers. They are assigned an encrypted alphanumeric string that all requests must come with to prove the origin and integrity of the request.
   * Virtual Private Network: this involves setting up a network that allows our servers and some third-party service providers to communicate over the internet; while being inaccessible to any requests outside that network. instead of direct server-to-server communication; we have a network-to-network interaction. NIBSS specifically is authenticated this way.

**Business Logic Layer:** this captures the processes that make the platform work
as it does. Some of them are implemented in PHP while others are in JAVA. Some
examples of these services are assessment, intelligence, cross-functions. Etc.

**Data Models:** these are data representations of the components that make the
platform work as it does.

.. figure:: /_static/images/data_model.png
   :alt: database module
   :align: center
   :width: 700

   *The database models and relationships*

**Database/Storage:** this is the final resting place of all data that go into the platform. It is powered by two *MySQL Databases*, one for backup and the other as the main database. Some data are saved directly to the server file system as "log.txt" files such as the results of chron services.

**Third-party APIs:** The system communicates with multiple third party APIs such as Twillio, MTN OPAY, NIBSS, Remita. See Full list of third party APIs :ref:`here! <thirdPartyAPIs>` 

.. Technologies
.. ++++++++++++

.. The Client side of PIRAS was built with Angular 8, the Server Side microservices were built with Codeigniter 4, and the primary database is MySQL.


.. toctree::
   :maxdepth: 2
   :caption: Contents: