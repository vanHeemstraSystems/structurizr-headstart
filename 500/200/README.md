# 200 Diagrams as Text

## Text as an architecture description language

There has been a trend over the past few years towards text-based tooling, with the most popular examples including [PlantUML](http://plantuml.com/), [WebSequenceDiagrams](https://www.websequencediagrams.com/) and [Mermaid](https://mermaid-js.github.io/mermaid/). With these tools, the diagram source is provided as text using a special domain-specific language, which the tool then visualises, typically with an automatic layout algorithm.

These tools generally have a low barrier to entry, and the source text is easily version controlled. Also, it's relatively straightforward to automate the use of these tools in order to generate diagrams and documentation during your build process.

However, each diagram needs to be defined separately, typically in a separate text file. If you have the same element on two diagrams, and you want to change the name of that element, you need to make sure that you change the name everywhere it's used. The global search and replace features in most developer tooling does make this less of a problem, but it's just one way that a collection of diagrams can easily become inconsistent if not managed properly.

To solve this problem, we can create a model (with multiple views) as text instead. For example, using the [Structurizr DSL](https://github.com/structurizr/dsl):

```
workspace "Getting Started" "This is a model of my software system." {

    model {
        user = person "User" "A user of my software system."
        softwareSystem = softwareSystem "Software System" "My software system."

        user -> softwareSystem "Uses"
    }

    views {
        systemContext softwareSystem "SystemContext" "An example of a System Context diagram." {
            include *
            autoLayout
        }

        styles {
            element "Software System" {
                background #1168bd
                color #ffffff
            }
            element "Person" {
                shape person
                background #08427b
                color #ffffff
            }
        }
    }

}
```

This definition creates a model containing elements and relationships, creates a single view, and adds some styling. This can be published to the Structurizr cloud service/on-premises installation via the [JSON-based web API](https://structurizr.com/help/web-api) using the [Structurizr CLI](https://github.com/structurizr/cli) tool.

[ See Image "getting-started" ]

[ See Image "getting-started-diagram-key" ]

A diagram key is automatically generated for you, based upon the [styles](https://structurizr.com/help/notation) and [shapes](https://structurizr.com/help/shapes) defined in the model.

## Multiple output formats
Rather than argue over which diagramming tool you're going to use, why not use them all? A huge benefit of creating software architecture models is that you can visualise the views in that model using ***multiple output formats***. For example, here are four versions of the same view (a C4 model container diagram), each created from the same model, and rendered in different diagramming tools.

[ See Image "" ]
PlantUML

[ See Image "" ]
Mermaid

[ See Image "" ]
Structurizr (traditional diagram)

[ See Image "" ]
Structurizr (diagram key)

[ See Image "" ]
Structurizr (graph visualisation)

You can also do the same with diagrams showing collaboration. Again, these were all generated from the same model, and rendered with different diagramming tools.

[ See Image "" ]
PlantUML

[ See Image "" ]
WebSequenceDiagrams

[ See Image "" ]
Mermaid

[ See Image "" ]
Mermaid

[ See Image "" ]
Structurizr (dynamic diagram)

[ See Image "" ]
Structurizr (diagram key)

## Benefits
In summary, the benefits of using text to create software architecture models with Structurizr include:

- ***Consistency***: Generating multiple diagrams from the same model ensures consistency, and details being in sync across diagrams.
- ***Multiple output formats***: Rather than being locked into a single tool, the Structurizr tooling provides a way to export your views to multiple formats.
- ***Versionable***: Since the models are text, they are also versionable alongside your codebase in your version control system.
- ***Living documentation***: The text to generate the model can be integrated with your automated build system to keep your models up to date; providing accurate, up-to-date, living software architecture diagrams that actually reflect the code.

## Implementations
The following implementations support the core concepts of the C4 model, and are compatible with the [web API](https://structurizr.com/help/web-api) used by the [Structurizr cloud service and on-premises installation](https://structurizr.com/). Diagrams can be rendered with Structurizr, or exported to PlantUML, Mermaid, and WebSequenceDiagrams formats using the [Structurizr CLI](https://github.com/structurizr/cli).

| Library | Input formats (create modesl using) |
| --- | --- |
| Structurizr DSL https://github.com/structurizr/dsl | Text-based domain specific language |
| Arch as code https://github.com/trilogy-group/arch-as-code | YAML |

See the GitHub repos linked above for getting started guides and examples. Looking for [diagrams as code](../100/README.md) instead?
