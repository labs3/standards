# Syv-02 - C4model

## Abstract

### Proposed use

Syvita will use the C4model to describe architectures for projects.

### Introduction

In short, the C4 model is a way of visualizing software using 4 levels. The important 4 elements are described below (of which we will use in our visualisation standard).

#### System Context (1)

On this level you only show who will be user of your system, what your system will do (in general) and in what environment it will work on (with what other systems it will have to interact).

#### Container (2)

On this level you zoom in a little bit and show of what kind of high level elements your system should be or will be built. As an example, we're gonna have Clarity contract(s), a frontend application and we also want to use Gaia in daoOS.

#### Component (3)

On this level you zoom in a little bit again and you show details of each of the elements from the container level. You want to show what kind of modules and/or components you want to have in each element.

Example: In daoOS, one was created for the Clarity contract.

#### Code (4)

Zoom in again, and this time you model every element from 3rd level using standard modeling techniques (mostly will be UML, ERD, Sequence diagrams etc.)

**Sources:**

- [C4model Website](https://c4model.com/)
- [YouTube tutorial by the author](https://www.youtube.com/watch?v=x2-rSnhpw0g&t)
- [Simon Brown's (2021) book](https://leanpub.com/b/software-architecture)

### Actual use (suggestion)

A suggestion for Syvita is to use draw.io to draw the diagrams and to share the working file (.drawio) in the docs folder of a project. Whenever a new version is uploaded an export of the diagrams as an image(s) (.png) should be included in the docs folder for easy viewing by all project members.

Note: In the future we could also consider drawing the diagrams in Miro, for more streamlined collaboration.

## Levels of visualization

C4model is a methodology to express software architectures in block diagram shapes. Effectively graphical notation or expressing language for modelling soft architectures.

### First level of visualization

The zoom-out perspective of the whole system in the biggest scale. Detail isn't important here as this is your zoomed out view showing a big picture of the system landscape. The focus should be on people (actors, roles, personas, etc) and software systems rather than technologies, protocols and other low-level details. It's the sort of diagram that you could show to non-technical people.

![Syv-02/c4model-1st%20level.png](./Syv-02/c4model-1st%20level.png)

So in short, each shape demonstrates the below meanings:
![Syv-02/c4model-1st%20level-2.png](./Syv-02/c4model-1st%20level-2.png)

**Example:** This is an example System Context diagram for a fictional Internet Banking System. It shows the people who use it, and the other software systems that the Internet Banking System has a relationship with. Personal Customers of the bank use the Internet Banking System to view information about their bank accounts and to make payments. The Internet Banking System itself uses the bank's existing Mainframe Banking System to do this, and uses the bank's existing E-mail System to send e-mails to customers.
![Syv-02/c4model-1st%20level-example.png](./Syv-02/c4model-1st%20level-example.png)

### Second level of visualization

Once you zoom in a bit, you are in the second level. This level of visualization is shown inside a dash-line boundary with **container** blocks. Once you understand how your system fits in to the overall IT environment, a really useful next step is to zoom in to the system boundary with a Container diagram.

![Syv-02/c4model-2nd%20level.png](./Syv-02/c4model-2nd%20level.png)

**Example:**
This is an example Container diagram for a fictional Internet Banking System. It shows that the Internet Banking System (the dashed box) is made up of five containers: a server-side Web Application, a Single-Page Application, a Mobile App, a server-side API Application, and a Database.

The Web Application is a Java/Spring MVC web application that simply serves static content (HTML, CSS and JavaScript), including the content that makes up the Single-Page Application.

The Single-Page Application is an Angular application that runs in the customer's web browser, providing all of the Internet banking features. Alternatively, customers can use the cross-platform Xamarin Mobile App, to access a subset of the Internet banking functionality.

Both the Single-Page Application and Mobile App use a JSON/HTTPS API, which is provided by another Java/Spring MVC application running on the server. The API Application gets user information from the Database (a relational database schema).

The API Application also communicates with the existing Mainframe Banking System, using a proprietary XML/HTTPS interface, to get information about bank accounts or make transactions. The API Application also uses the existing E-mail System if it needs to send e-mails to customers.

![Syv-02/c4model-2nd%20level-example.png](./Syv-02/c4model-2nd%20level-example.png)

### Third level of visualisation

You can zoom in more into level-2 containers/blocks to show how a container is made up of several "components"...

Symbol diagrams below listed:
![Syv-02/c4model-3rd%20level.png](./Syv-02/c4model-3rd%20level.png)

**Example:**

This is an example Component diagram for a fictional Internet Banking System, showing some (rather than all) of the components within the API Application.

Here, there are three Spring MVC Rest Controllers providing access points for the JSON/HTTPS API, with each controller subsequently using other components to access data from the Database and Mainframe Banking System, or send e-mails.

![Syv-02/c4model-3rd%20level-example.png](./Syv-02/c4model-3rd%20level-example.png)

### Fourth level of visualization

To zoom in to see the codes. This is an optional level of detail and is often available on-demand from tooling such as IDEs.

This is an example (and partial) UML class diagram for a fictional Internet Banking System, showing the code elements (interfaces and classes) that make up the MainframeBankingSystemFacade component. It shows that the component is made up of some classes, with the implementation details directly reflecting the code.
![Syv-02/c4model-4th%20level-example.png](./Syv-02/c4model-4th%20level-example.png)

## Notations

There are several subtleties of importance in regards to the c4-model.

### Put titles on pages

Type of diagram and purpose must always be included.

Short and meaningful, include the diagram type, numbered if diagram order is important; for example:

**System context diagram** for Financial Risk System

[System context] Financial Risk System

### Visual consistency

For example keep the colors consistent in all levels of the diagram and keep objects in the same general location for example people once placed left centre, keep them there.

Be consistent with notation and element positioning across diagrams: keeping people in the same general location for example and use the same color coding.

*Shape, color and size are used to complement a diagram that already makes sense.*

### Acronyms

Be careful to use acronyms/abbreviations. It will be much easier for new people to onboard if we do not use any abbreviations but that may be to much to ask, lets at least try to avoid making Syvita/project specific abbreviations.

### Elements (boxes)

Start with: simple boxes containing the (A) element name, (B) type, (C) technology (if applicable) and (D) a description/responsibilities.
When you make the first draft do not worry about shape and color. That will come later according to the examples above.

**D. is where the C4 model distinguishes itself from other architecture diagrams these descriptions will help a lot with making these diagrams useful and readable. The description can be a sentence and also 5-7 bullet points to list out the key responsibilities of that element.**

![c4-model-four-types_of_elements](https://user-images.githubusercontent.com/33360391/116086202-d811fb00-a69f-11eb-85e1-3c32b14354a9.png)

### Lines

Uni-directional lines only is preferred (arrows always point one way). Which way you point them is up to you. Usually something along the line of "thing a calls → thing b" or thing a depends  on → thing b". Just make sure that the direction of the arrow matches the text on the arrow that describes it.

Most of the times when you think you need two lines for example

Thing A **makes an API request to** —> Thing B

Thing A <— **sends and API response to** Thing B

Can be easy replaced by one arrow even if the direction is bidirectional, the text of the arrow makes the intent known avoiding arrow clutter.

Thing A  **Makes API calls using** —> Thing B

If there are two relationships between boxes that have completely different intents it is of course alright to show two arrows.

### Key/Legend

Explain shapes, line styles, colours, borders, acronyms, etc... even if we have a standard and the notation seems obvious.
