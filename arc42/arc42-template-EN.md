#

**About arc42**

arc42, the template for documentation of software and system
architecture.

Template Version 8.2 EN. (based upon AsciiDoc version), January 2023

Created, maintained and © by Dr. Peter Hruschka, Dr. Gernot Starke and
contributors. See <https://arc42.org>.

<div class="note">

This version of the template contains some help and explanations. It is
used for familiarization with arc42 and the understanding of the
concepts. For documentation of your own system you use better the
_plain_ version.

</div>

<div style="page-break-after: always;"></div>

<hr>
<br>

# 1. Introduction and Goals

The following arc42 template deals with the architecture and documentation of an "Image Sharing App". We are a team of dedicated professionals, working for a regional technology company.

Team members are:

Alexander B.  
Alireza J.  
Carolin M.

## 1.1. Requirements Overview

<div class="formalpara-title">

**What is the Image Sharing App?**  
The main purpose is an image sharing app targeting photography enthusiasts and professionals, with a strong community aspect.

**Main features**

- Register and login
- Upload and share images
- Like images
- Comment on images
- Advanced editing through a third party integration with Pixlr
- Make, use and save custom image filters
- Social feed for following other users
- Free tier with limited features and subscription model for full access

The app must be able to handle a large concurrent user base.

</div>

## 1.2. Quality Goals

<div class="formalpara-title">

Table 1. Quality Goals

| Priority | Quality     | Motivation                                                                                                                    |
| -------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1        | Usability   | The app must be user-friendly and easy to navigate The subscription model must be clearly communicated and easy to understand |
| 2        | Reliability | The app must be stable and function without significant bugs or errors                                                        |
| 3        | Performance | The app must be optimized for performance and load times                                                                      |

</div>

## 1.3. Stakeholders

<div class="formalpara-title">

The following lists contains the most important personas for this application

Table 2. Stakeholders

| Role/Name                                                  | Expectations                                                                                                                                                                                                  |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Marketing Manager, Sarah Chen, Bold Branding Agency        | Expecting that the features of the application match the needs of the market, that the app is attractive to the target audience so that commercialisation and marketing campaigns are successful.             |
| Project Manager, Michael Nguyen, Digital Dreams Inc.       | Expecting that the development of the app meets the timeframe and scope to manage deadlines, meetings and costs; Management of optimal use of resources; Focus on communication and collaboration of the team |
| Lead Developer, Ava Patel, Pixel Perfect Solutions         | High quality of application development, clear idea of the architecture, clear documentation; Prioritizing quality goals in application development;                                                          |
| UX/UI Designer, Emily Wong, Creative Co.                   | intuitive and attractive user interface with a focus on usability                                                                                                                                             |
| User Representative, Samir Singh, Photography Enthusiast   | easy and intuitive usability, users' wishes are fulfilled, high reliability (no crashes or errors)                                                                                                            |
| Photography Expert, Lucas Rodriguez, Snap & Shoot Magazine | Testing the application and ensuring that the specific features of the application meet the needs of professional photographers.                                                                              |

</div>

<div style="page-break-after: always;"></div>

<hr>
<br>

# 2. Architecture Constraints

<div class="formalpara-title">

| Constraints                 | Background and/or motivation                                                                                                                                       |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Storage and Data Management | Because of high-quality images, each user should have a memory limitation; Cloud based storage; Efficient Data retrieval: efficient search and retrieval of images |
| Multi-Language-support      | Because it is a regional project in Austria, it should support both german and english                                                                             |
| Third-party-integration     | The integration of the third-party service (Pixlr) puts some constraints on the features of the application, ensure efficient API management                       |
| Budgetary Limitations       | available budget constraints the scale of infrastructure, and the acquisition of third-party services                                                              |
| Platform Compatibility      | The application should work on IOS                                                                                                                                 |

**Contents**

</div>

Any requirement that constraints software architects in their freedom of
design and implementation decisions or decision about the development
process. These constraints sometimes go beyond individual systems and
are valid for whole organizations and companies.

<div class="formalpara-title">

**Motivation**

</div>

Architects should know exactly where they are free in their design
decisions and where they must adhere to constraints. Constraints must
always be dealt with; they may be negotiable, though.

<div class="formalpara-title">

**Form**

</div>

Simple tables of constraints with explanations. If needed you can
subdivide them into technical constraints, organizational and political
constraints and conventions (e.g. programming or versioning guidelines,
documentation or naming conventions)

See [Architecture Constraints](https://docs.arc42.org/section-2/) in the
arc42 documentation.

<div style="page-break-after: always;"></div>

<hr>
<br>

# 3. System Scope and Context

<div class="formalpara-title">

**Contents**

</div>

System scope and context - as the name suggests - delimits your system
(i.e. your scope) from all its communication partners (neighboring
systems and users, i.e. the context of your system). It thereby
specifies the external interfaces.

If necessary, differentiate the business context (domain specific inputs
and outputs) from the technical context (channels, protocols, hardware).

<div class="formalpara-title">

**Motivation**

</div>

The domain interfaces and technical interfaces to communication partners
are among your system’s most critical aspects. Make sure that you
completely understand them.

<div class="formalpara-title">

**Form**

</div>

Various options:

- Context diagrams

- Lists of communication partners and their interfaces.

See [Context and Scope](https://docs.arc42.org/section-3/) in the arc42
documentation.

## 3.1. Business Context

<div class="formalpara-title">

<table border="1">
    <tr>
        <th>Communication Partner</th>
        <th>Interfaces</th>
        <th>Inputs</th>
        <th>Outputs</th>
    </tr>
    <tr>
        <td>Users</td>
        <td>Mobile App, User Interface, social feed</td>
        <td>User credentials, image upload, comments, likes</td>
        <td>shared images, notifications</td>
    </tr>
    <tr>
        <td>IT-Systems (Pixlr)</td>
        <td>Pixlr Integration, Image Editing</td>
        <td>Image data, filter settings</td>
        <td>edited images, processing status</td>
    </tr>
    <tr>
        <td>Cloud provider</td>
        <td>Cloud Storage APIs</td>
        <td>Image storage and retrieval</td>
        <td>Scalable image storage solution</td>
    </tr>
    <tr>
        <td>Subscription System</td>
        <td>Payment Gateway, Subscription Management</td>
        <td>User subscriptions, payment details</td>
        <td>Full access permissions</td>
    </tr>
    <tr>
        <td>Social Media Platforms</td>
        <td>Social Media APIs</td>
        <td>User shared content</td>
        <td>Increased app visibility, user acquisition</td>
    </tr>
    <tr>
        <td>Marketing Manager</td>
        <td>Marketing Campaign, Analytics Integration</td>
        <td>Marketing data, campaign details</td>
        <td>user engagement data</td>
    </tr>
    <tr>
        <td>UX/UI Designer</td>
        <td>UI/UX Design, Design Tools</td>
        <td>Design mockups, User feedback</td>
        <td>UI/UX improvements, usability metrics</td>
    </tr>
</table>

</div>

Specification of **all** communication partners (users, IT-systems, …)
with explanations of domain specific inputs and outputs or interfaces.
Optionally you can add domain specific formats or communication
protocols.

<div class="formalpara-title">

**Motivation**

</div>

All stakeholders should understand which data are exchanged with the
environment of the system.

<div class="formalpara-title">

**Form**

</div>

All kinds of diagrams that show the system as a black box and specify
the domain interfaces to communication partners.

Alternatively (or additionally) you can use a table. The title of the
table is the name of your system, the three columns contain the name of
the communication partner, the inputs, and the outputs.

**\<Diagram or Table>**

**\<optionally: Explanation of external domain interfaces>**

## 3.2. Technical Context

<div class="formalpara-title">

**Contents**

</div>

Technical interfaces (channels and transmission media) linking your
system to its environment. In addition a mapping of domain specific
input/output to the channels, i.e. an explanation which I/O uses which
channel.

<div class="formalpara-title">

**Motivation**

</div>

Many stakeholders make architectural decision based on the technical
interfaces between the system and its context. Especially infrastructure
or hardware designers decide these technical interfaces.

<div class="formalpara-title">

**Form**

</div>

E.g. UML deployment diagram describing channels to neighboring systems,
together with a mapping table showing the relationships between channels
and input/output.

**\<Diagram or Table>**

**\<optionally: Explanation of technical interfaces>**

**\<Mapping Input/Output to Channels>**

<div style="page-break-after: always;"></div>

<hr>
<br>

# 4. Solution Strategy

<div class="formalpara-title">

<table border="1">
    <tr>
        <th>Goal/Requirements</th>
        <th>Architectural Approach</th>
    </tr>
    <tr>
        <td>Scalability</td>
        <td>Microservices</td>
    </tr>
    <tr>
        <td>Performance</td>
        <td>Caching Strategies and Content Delivery Networks (CDN)</td>
    </tr>
    <tr>
        <td>Reliability</td>
        <td>Redundancy and Load Balancing</td>
    </tr>
</table>

</div>

A short summary and explanation of the fundamental decisions and
solution strategies, that shape system architecture. It includes

- technology decisions

- decisions about the top-level decomposition of the system, e.g.
  usage of an architectural pattern or design pattern

- decisions on how to achieve key quality goals

- relevant organizational decisions, e.g. selecting a development
  process or delegating certain tasks to third parties.

<div class="formalpara-title">

**Motivation**

</div>

These decisions form the cornerstones for your architecture. They are
the foundation for many other detailed decisions or implementation
rules.

<div class="formalpara-title">

**Form**

</div>

Keep the explanations of such key decisions short.

Motivate what was decided and why it was decided that way, based upon
problem statement, quality goals and key constraints. Refer to details
in the following sections.

See [Solution Strategy](https://docs.arc42.org/section-4/) in the arc42
documentation.

<div style="page-break-after: always;"></div>

<hr>
<br>

# 5. Building Block View

<div class="formalpara-title">

**Content**

</div>

The building block view shows the static decomposition of the system
into building blocks (modules, components, subsystems, classes,
interfaces, packages, libraries, frameworks, layers, partitions, tiers,
functions, macros, operations, data structures, …) as well as their
dependencies (relationships, associations, …)

This view is mandatory for every architecture documentation. In analogy
to a house this is the _floor plan_.

<div class="formalpara-title">

**Motivation**

</div>

Maintain an overview of your source code by making its structure
understandable through abstraction.

This allows you to communicate with your stakeholder on an abstract
level without disclosing implementation details.

<div class="formalpara-title">

**Form**

</div>

The building block view is a hierarchical collection of black boxes and
white boxes (see figure below) and their descriptions.

![Hierarchy of building blocks](images/05_building_blocks-EN.png)

**Level 1** is the white box description of the overall system together
with black box descriptions of all contained building blocks.

**Level 2** zooms into some building blocks of level 1. Thus it contains
the white box description of selected building blocks of level 1,
together with black box descriptions of their internal building blocks.

**Level 3** zooms into selected building blocks of level 2, and so on.

See [Building Block View](https://docs.arc42.org/section-5/) in the
arc42 documentation.

## 5.1. Whitebox Overall System

Here you describe the decomposition of the overall system using the
following white box template. It contains

- an overview diagram

- a motivation for the decomposition

- black box descriptions of the contained building blocks. For these
  we offer you alternatives:

  - use _one_ table for a short and pragmatic overview of all
    contained building blocks and their interfaces

  - use a list of black box descriptions of the building blocks
    according to the black box template (see below). Depending on
    your choice of tool this list could be sub-chapters (in text
    files), sub-pages (in a Wiki) or nested elements (in a modeling
    tool).

- (optional:) important interfaces, that are not explained in the
  black box templates of a building block, but are very important for
  understanding the white box. Since there are so many ways to specify
  interfaces why do not provide a specific template for them. In the
  worst case you have to specify and describe syntax, semantics,
  protocols, error handling, restrictions, versions, qualities,
  necessary compatibilities and many things more. In the best case you
  will get away with examples or simple signatures.

**_\<Overview Diagram>_**

Motivation  
_\<text explanation>_

Contained Building Blocks  
_\<Description of contained building block (black boxes)>_

Important Interfaces  
_\<Description of important interfaces>_

Insert your explanations of black boxes from level 1:

If you use tabular form you will only describe your black boxes with
name and responsibility according to the following schema:

| **Name**         | **Responsibility** |
| ---------------- | ------------------ |
| _\<black box 1>_ |  *\<Text>*         |
| _\<black box 2>_ |  *\<Text>*         |

If you use a list of black box descriptions then you fill in a separate
black box template for every important building block . Its headline is
the name of the black box.

### \<Name black box 1>

Here you describe \<black box 1> according the the following black box
template:

- Purpose/Responsibility

- Interface(s), when they are not extracted as separate paragraphs.
  This interfaces may include qualities and performance
  characteristics.

- (Optional) Quality-/Performance characteristics of the black box,
  e.g.availability, run time behavior, ….

- (Optional) directory/file location

- (Optional) Fulfilled requirements (if you need traceability to
  requirements).

- (Optional) Open issues/problems/risks

_\<Purpose/Responsibility>_

_\<Interface(s)>_

_\<(Optional) Quality/Performance Characteristics>_

_\<(Optional) Directory/File Location>_

_\<(Optional) Fulfilled Requirements>_

_\<(optional) Open Issues/Problems/Risks>_

### \<Name black box 2>

_\<black box template>_

### \<Name black box n>

_\<black box template>_

### \<Name interface 1>

…

### \<Name interface m>

## 5.2. Level 2

Here you can specify the inner structure of (some) building blocks from
level 1 as white boxes.

You have to decide which building blocks of your system are important
enough to justify such a detailed description. Please prefer relevance
over completeness. Specify important, surprising, risky, complex or
volatile building blocks. Leave out normal, simple, boring or
standardized parts of your system

### White Box _\<building block 1>_

…describes the internal structure of _building block 1_.

_\<white box template>_

### White Box _\<building block 2>_

_\<white box template>_

…

### White Box _\<building block m>_

_\<white box template>_

## 5.3. Level 3

Here you can specify the inner structure of (some) building blocks from
level 2 as white boxes.

When you need more detailed levels of your architecture please copy this
part of arc42 for additional levels.

### White Box \<\_building block x.1\_\>

Specifies the internal structure of _building block x.1_.

_\<white box template>_

### White Box \<\_building block x.2\_\>

_\<white box template>_

### White Box \<\_building block y.1\_\>

_\<white box template>_

<div style="page-break-after: always;"></div>

<hr>
<br>

# 6. Runtime View

<div class="formalpara-title">

**Contents**

</div>

The runtime view describes concrete behavior and interactions of the
system’s building blocks in form of scenarios from the following areas:

- important use cases or features: how do building blocks execute
  them?

- interactions at critical external interfaces: how do building blocks
  cooperate with users and neighboring systems?

- operation and administration: launch, start-up, stop

- error and exception scenarios

Remark: The main criterion for the choice of possible scenarios
(sequences, workflows) is their **architectural relevance**. It is
**not** important to describe a large number of scenarios. You should
rather document a representative selection.

<div class="formalpara-title">

**Motivation**

</div>

You should understand how (instances of) building blocks of your system
perform their job and communicate at runtime. You will mainly capture
scenarios in your documentation to communicate your architecture to
stakeholders that are less willing or able to read and understand the
static models (building block view, deployment view).

<div class="formalpara-title">

**Form**

</div>

There are many notations for describing scenarios, e.g.

- numbered list of steps (in natural language)

- activity diagrams or flow charts

- sequence diagrams

- BPMN or EPCs (event process chains)

- state machines

- …

See [Runtime View](https://docs.arc42.org/section-6/) in the arc42
documentation.

## \<Runtime Scenario 1>

- _\<insert runtime diagram or textual description of the scenario>_

- _\<insert description of the notable aspects of the interactions
  between the building block instances depicted in this diagram.>_

## \<Runtime Scenario 2>

## …

## \<Runtime Scenario n>

<div style="page-break-after: always;"></div>

<hr>
<br>

# 7. Deployment View

<div class="formalpara-title">

**Content**

</div>

The deployment view describes:

1.  technical infrastructure used to execute your system, with
    infrastructure elements like geographical locations, environments,
    computers, processors, channels and net topologies as well as other
    infrastructure elements and

2.  mapping of (software) building blocks to that infrastructure
    elements.

Often systems are executed in different environments, e.g. development
environment, test environment, production environment. In such cases you
should document all relevant environments.

Especially document a deployment view if your software is executed as
distributed system with more than one computer, processor, server or
container or when you design and construct your own hardware processors
and chips.

From a software perspective it is sufficient to capture only those
elements of an infrastructure that are needed to show a deployment of
your building blocks. Hardware architects can go beyond that and
describe an infrastructure to any level of detail they need to capture.

<div class="formalpara-title">

**Motivation**

</div>

Software does not run without hardware. This underlying infrastructure
can and will influence a system and/or some cross-cutting concepts.
Therefore, there is a need to know the infrastructure.

Maybe a highest level deployment diagram is already contained in section
3.2. as technical context with your own infrastructure as ONE black box.
In this section one can zoom into this black box using additional
deployment diagrams:

- UML offers deployment diagrams to express that view. Use it,
  probably with nested diagrams, when your infrastructure is more
  complex.

- When your (hardware) stakeholders prefer other kinds of diagrams
  rather than a deployment diagram, let them use any kind that is able
  to show nodes and channels of the infrastructure.

See [Deployment View](https://docs.arc42.org/section-7/) in the arc42
documentation.

## Infrastructure Level 1

Describe (usually in a combination of diagrams, tables, and text):

- distribution of a system to multiple locations, environments,
  computers, processors, .., as well as physical connections between
  them

- important justifications or motivations for this deployment
  structure

- quality and/or performance features of this infrastructure

- mapping of software artifacts to elements of this infrastructure

For multiple environments or alternative deployments please copy and
adapt this section of arc42 for all relevant environments.

**_\<Overview Diagram>_**

Motivation  
_\<explanation in text form>_

Quality and/or Performance Features  
_\<explanation in text form>_

Mapping of Building Blocks to Infrastructure  
_\<description of the mapping>_

## Infrastructure Level 2

Here you can include the internal structure of (some) infrastructure
elements from level 1.

Please copy the structure from level 1 for each selected element.

### _\<Infrastructure Element 1>_

_\<diagram + explanation>_

### _\<Infrastructure Element 2>_

_\<diagram + explanation>_

…

### _\<Infrastructure Element n>_

_\<diagram + explanation>_

<div style="page-break-after: always;"></div>

<hr>
<br>

## 8. Cross-cutting Concepts

### 8.1 Domain Concepts

Our application adopts a domain-driven design to allow developers and business experts to collaborate more efficiently.

### 8.2 User Experience (UX) Concepts

- **Responsive Design**
- **Intuitive Navigation**
- **Error Handling**

### 8.3 Safety and Security Concepts

We implement comprehensive authentication mechanisms, often considering OAuth2 for secure access management. Data protection is enhanced through:

- **Encryption for sensitive data**
- **Compliance to the Digital Service Act** TODO: look up other relevant laws?

### 8.4 Architecture and Design Patterns

#### Frontend Using React Native

- **Pattern:** TODO: MVC? Command pattern?
- **Component-Based Structure:** Reusable UI components and efficient state management.

#### Backend Using Node.js

- **Microservices Architecture for scalability and ease of maintanance**
- **RESTful APIs for decoupling communication between frontend and backend services**

### 8.5 "Under-the-Hood"

TODO: choose database. We use AWS for hosting, taking advantage of their scalability and reliability.

### 8.6 Development Concepts

We adhere to **Agile methodologies**, encouraging iterative development and incorporating regular stakeholder feedback. Our development practices include:

- **Git for Version Control and Peer-Reviews**
- **CI/CD Pipelines with automated testing and deployment**

### 8.7 Operational Concepts

Our operational strategy includes:

- **Docker for Containerization**
- **Robust Logging for error tracking and diagnosis**

<div style="page-break-after: always;"></div>

<hr>
<br>

# 9. Architecture Decisions

<div class="formalpara-title">

<table border="1">
    <tr>
        <th>Problem</th>
        <th>Considered Alternatives</th>
        <th>Decision</th>
    </tr>
    <tr>
        <td>Large number of users/images</td>
        <td>
            <ul>
                <li>Micro Services</li>
                <li>Monolithic</li>
            </ul>
        </td>
        <td>Micro Services, because of scalability and reliability in a scaling scenario</td>
    </tr>
    <tr>
        <td>Optimizing Image Loading Performance</td>
        <td>
            <ul>
                <li>Synchronous Image Loading</li>
                <li>Asynchronous Image Loading with Caching</li>
            </ul>
        </td>
        <td>Asynchronous, because of faster loading, smoother user experience, reduced waiting.</td>
    </tr>
    <tr>
        <td>Ensuring High Availability in Case of Server Failures</td>
        <td>
            <ul>
                <li>Single Server with Failover Mechanism</li>
                <li>Load Balancing across Multiple Servers</li>
            </ul>
        </td>
        <td>Load Balancing, because of enhanced reliability, prevents overloading, ensures availability.</td>
    </tr>
</table>
</br>

</div>

<div style="page-break-after: always;"></div>

<hr>
<br>

# 10. Quality Requirements

## 10.1. Quality Tree

<div class="formalpara-title">

![Hierarchy of building blocks](images/09_Quality_tree.png)

</div>

## 10.2. Quality Scenarios

<div class="formalpara-title">

**Usability**

</div>

Scenario 1: A new user attempts to register and create a profile.

The user has instaled the app and opened it for the first time. When the user navigates to the registration screen, the registration process should be easily understandable and the user should complete the registration process without assistance.

Scenario 2: A user explores subscription options.

An existing user is interested in premium features. When the user navigates to the subscription information section, the subscription options should be clearly presented, with differences between tiers easily understandable.

<div class="formalpara-title">

**Reliability**

</div>

Scenario 1: Handling high concurrent user load.

A significant number of users are accessing the app simultaneously. When users are uploading, editing, and sharing images, the app should function smoothly without crashing or significant lag.

Scenario 2: Recovering from a server failure.

One of the servers hosting the app fails. The failure occurs during peak usage hours. Then the system should automatically reroute traffic to other servers, ensuring uninterrupted service for users.

<div class="formalpara-title">

**Performance**

</div>

Scenario 1: Image upload and retrieval speed.

A user selects a high-resolution image to upload. When the user uploads the image, it should be uploaded and available for viewing in a reasonable amount of time.

Scenario 2: Response time during peak usage.

The app is experiencing peak traffic. When a user performs an action requiring server response, the action should complete within a few seconds, even under high load.

<div style="page-break-after: always;"></div>

<hr>
<br>

# 11. Risks and Technical Debts

<div class="formalpara-title">

<table border="1">
    <tr>
        <th>Risk/Technical Debt</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>reliance on third-party service (Pixlr)</td>
        <td>Pixlr downtime limits app's image editing functionality; Implement failover: multiple external services, local/hosted image editing backups.</td>
    </tr>
    <tr>
        <td>Data security and privacy compliance</td>
        <td>Security risks: data breaches, legal implications possible; Regular audits, encryption, access control, and policies</td>
    </tr>
    <tr>
        <td>Performance reduction due to unoptimized image sharing</td>
        <td>Performance reduction as the user base grows and image uploads increase; Utilize image compression techniques to decrease file sizes without compromising quality; Regular performance testing and optimization</td>
    </tr>
</table>
</div>
</br>
<!-- A list of identified technical risks or technical debts, ordered by
priority

<div class="formalpara-title">

**Motivation**

</div>

“Risk management is project management for grown-ups” (Tim Lister,
Atlantic Systems Guild.)

This should be your motto for systematic detection and evaluation of
risks and technical debts in the architecture, which will be needed by
management stakeholders (e.g. project managers, product owners) as part
of the overall risk analysis and measurement planning.

<div class="formalpara-title">

**Form**

</div>

List of risks and/or technical debts, probably including suggested
measures to minimize, mitigate or avoid risks or reduce technical debts.

See [Risks and Technical Debt](https://docs.arc42.org/section-11/) in
the arc42 documentation.

<div style="page-break-after: always;"></div> -->

<hr>
<br>

# 12. Glossary

<div class="formalpara-title">

**Contents**

</div>

The most important domain and technical terms that your stakeholders use
when discussing the system.

You can also see the glossary as source for translations if you work in
multi-language teams.

<div class="formalpara-title">

**Motivation**

</div>

You should clearly define your terms, so that all stakeholders

- have an identical understanding of these terms

- do not use synonyms and homonyms

A table with columns \<Term> and \<Definition>.

Potentially more columns in case you need translations.

See [Glossary](https://docs.arc42.org/section-12/) in the arc42
documentation.

| Term        | Definition        |
| ----------- | ----------------- |
| _\<Term-1>_ | _\<definition-1>_ |
| _\<Term-2>_ | _\<definition-2>_ |
