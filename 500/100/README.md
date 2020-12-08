# 100 Diagrams as Code

Java, .NET, TypeScript, PHP, Python, and Go via the JSON web API

[ See Image "modelling-code" ]

```

```

## Code as an executable architecture description language

There has been a trend over the past few years towards text-based tooling, with the most popular examples including [PlantUML](http://plantuml.com/), [WebSequenceDiagrams](https://www.websequencediagrams.com/) and [Mermaid](https://mermaid-js.github.io/mermaid/). With these tools, the diagram source is provided as text using a special domain-specific language, which the tool then visualises, typically with an automatic layout algorithm.

These tools generally have a low barrier to entry, and the source text is easily version controlled. Also, it's relatively straightforward to automate the use of these tools in order to generate diagrams and documentation during your build process.

However, each diagram needs to be defined separately, typically in a separate text file. If you have the same element on two diagrams, and you want to change the name of that element, you need to make sure that you change the name everywhere it's used. The global search and replace features in most developer tooling does make this less of a problem, but it's just one way that a collection of diagrams can easily become inconsistent if not managed properly.

When you think about it, code is just text, and another type of domain-specific language. The ***open source Structurizr client libraries*** allow you to create your software architecture model, and associated documentation, via code. For example, using Structurizr for Java:

```
public static void main(String[] args) throws Exception {
    Workspace workspace = new Workspace("Getting Started", "This is a model of my software system.");
    Model model = workspace.getModel();

    Person user = model.addPerson("User", "A user of my software system.");
    SoftwareSystem softwareSystem = model.addSoftwareSystem("Software System", "My software system.");
    user.uses(softwareSystem, "Uses");

    ViewSet viewSet = workspace.getViews();
    SystemContextView contextView = viewSet.createSystemContextView(softwareSystem, "SystemContext", "An example of a System Context diagram.");
    contextView.addAllSoftwareSystems();
    contextView.addAllPeople();

    Styles styles = viewSet.getConfiguration().getStyles();
    styles.addElementStyle(Tags.SOFTWARE_SYSTEM).background("#1168bd").color("#ffffff");
    styles.addElementStyle(Tags.PERSON).background("#08427b").color("#ffffff").shape(Shape.Person);

    StructurizrClient structurizrClient = new StructurizrClient("key", "secret");
    structurizrClient.putWorkspace(25441, workspace);
}
```

This program creates a model containing elements and relationships, creates a single view, adds some styling, and uploads it to the Structurizr cloud service/on-premises installation via the [JSON-based web API](https://structurizr.com/help/web-api).

[ See Image "getting-started"  ]

[ See Image "getting-started-diagram-key"  ]

A diagram key is automatically generated for you, based upon the [styles](https://structurizr.com/help/notation) and [shapes](https://structurizr.com/help/shapes) defined in the model.

This code, which was used to create the software architecture model, can be thought of as an ***executable domain specific language***, or an ***executable architecture description language***. Using code provides a number of unique opportunities over using a static textual description:

- Use reflection and static analysis techniques to "extract" components from your production codebase, based upon naming conventions or machine readable metadata (e.g. Java Annotations, C# Attributes, etc).
- Parse log files or observability data to create a model of your distributed/microservices architecture.
- Parse CloudFormation or Terraform scripts to create a model of your distributed/microservices architecture.
- Extract the dependency graph from your central application/service register to create a model of your system landscape.
- Parse software architecture model definitions from other tools.
- Parse software architecture model definitions from other formats (e.g. plain text, YAML, XML, etc).
Some of these features are available out of the box with some of the client library implementations, others you will need to build yourself.

## Multiple output formats

Rather than argue over which diagramming tool you're going to use, why not use them all? A huge benefit of creating software architecture models is that you can visualise the views in that model using ***multiple output formats***. For example, here are four versions of the same view (a C4 model container diagram), each created from the same model, and rendered in different diagramming tools.

[ See Image "structurizr-36141-Containers-plantuml" ]
PlantUML

[ See Image "structurizr-36141-Containers-structurizr" ]
Structurizr (traditional diagram)

[ See Image "structurizr-36141-Containers-structurizr-key" ]
Structurizr (diagram key)

[ See Image "structurizr-36141-Containers-mermaid" ]
Mermaid

[ See Image "structurizr-36141-Containers-structurizr-graph" ]
Struturizr (graph visualisation)

You can also do the same with diagrams showing collaboration. Again, these were all generated from the same model, and rendered with different diagramming tools.

[ See Image "structurizr-36141-SignIn-plantuml" ]
PlantUML

[ See Image "structurizr-36141-SignIn-websequencediagrams" ]
WebSequenceDiagrams

[ See Image "structurizr-36141-SignIn-mermaid" ]
Mermaid

[ See Image "structurizr-36141-SignIn-structurizr" ]
Structurizr (dynamic diagram)

[ See Image "structurizr-36141-SignIn-structurizr-key" ]
Structurizr (diagram key)

## Benefits
In summary, the benefits of using code to create software architecture models with Structurizr include:

- ***Consistency***: Generating multiple diagrams from the same model ensures consistency, and details being in sync across diagrams.
- ***Code is familiar***: Code is familiar to us as software developers, so let's take advantage of this rather than creating another language with which to represent a software architecture model.
- ***Flexibility for creating models***: In addition to manually writing code to create a software architecture model, we can also write code to extract architectural concepts (e.g. components) from our production codebase using techniques such as reflection, introspection and static analysis.
- ***Multiple output formats***: Rather than being locked into a single tool, creating your model as code provides a way to export your views to multiple formats.
- ***Flexibility for visualising models***: Writing code to create the views of a software architecture model provides you with the ability to slice and dice the model as needed. For example, showing all components for a large system will result in a very cluttered diagram. Instead, you can simply write some code to programmatically create a number of smaller, simpler diagrams; perhaps one per vertical slice, web controller, user story, etc. You can also opt to include or exclude any elements as necessary.
- ***Versionable***: Since the models are code, they are also versionable alongside your codebase in your version control system.
- ***Living documentation***: The code to generate the model can be integrated with your automated build system to keep your models up to date; providing accurate, up-to-date, living software architecture diagrams that actually reflect the code.

## Implementations
The following implementations support the core concepts of the C4 model, and are compatible with the web API used by the Structurizr cloud service and on-premises installation. Diagrams can be rendered with Structurizr, or exported to PlantUML and WebSequenceDiagrams formats using the Structurizr CLI.

| Library | Input formats (create modesl using) |
| --- | --- |
| Structurizr for Java https://github.com/structurizr/java | Java and other JVM compatible languages (e.g. Groovy, Kotlin, Scala) |
| Structurizr for .NET https://github.com/structurizr/dotnet | .NET compatible languages(Framework and Core) |
| Structurizr for TypeScript https://github.com/ChristianEder/structurizr-typescript | TypeScript |
| Structurizr for PHP https://github.com/structurizr-php/structurizr-php | PHP |
| Structurizr for Python https://github.com/Midnighter/structurizr-python | Python |
| Structurizr for Go https://github.com/goadesign/structurizr | Go |

See the GitHub repos linked above for getting started guides and code examples. Looking for [diagrams as text](../200/README.md) instead?
