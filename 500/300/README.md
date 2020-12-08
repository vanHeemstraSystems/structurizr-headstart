# 300 Browser-based UI

A web-based UI; recommended for non-programmers

## Workspace editor

The workspace editor allows you to create and modify elements, relationships, views and more.

[ See Image "editor-screenshot-1" ]

View and manage the hierarchy of elements that make up the static structure.

[ See Image "editor-screenshot-2" ]

View and manage the relationships between elements in the model.

[ See Image "editor-screenshot-3" ]

Modify the set of diagrams and their content.

[ See Image "editor-screenshot-4" ]

Modify the styles used on your diagrams.

To use the workspace editor, click the  label/button on your dashboard or workspace summary page.

[DEMO](https://structurizr.com/ui)

## Getting started
Here's a short getting started guide to using the browser-based workspace editor. This is equivalent to the getting started examples for the [Structurizr for Java](https://github.com/structurizr/java/blob/master/docs/getting-started.md) and [Structurizr for .NET](https://github.com/structurizr/dotnet/blob/master/docs/getting-started.md) client libraries. Click a screenshot to enlarge it.

[ See Image "getting-started-editor-01" ]

Open the workspace editor for your workspace.

[ See Image "getting-started-editor-02" ]

Click on the black circle representing the workspace (in this case, it's labelled "Getting Started"). This will open a modal where we can add a software system or a person. Fill in the name and description fields, and click on the "Add person" button.

[ See Image "getting-started-editor-03" ]

This will add a person element to the model, which you can see in the tree structure.

[ See Image "getting-started-editor-04" ]

Now repeat the process to create a software system, and click the "Add software system" button.

[ See Image "getting-started-editor-05" ]

Now we have two elements in the model; one person, and one software system.

[ See Image "getting-started-editor-06" ]

Now click on the "Relationships" tab.

[ See Image "getting-started-editor-07" ]

Click once on the person element, and a second time on the software system element. This opens a modal where we can create a relationship between the two elements. Fill in the description field, and click the "Add relationship" button.

[ See Image "getting-started-editor-08" ]

This will add a relationship between the two elements in the model, as reflected by the arrow between the nodes.

[ See Image "getting-started-editor-09" ]

Now click on the "Views" tab.

[ See Image "getting-started-editor-10" ]

Click the "+ System Context View" button. This opens a modal where can can create a System Context view for our software system. Fill in the key (a short identifier for the view), and description fields. Click the "Create" button.

[ See Image "getting-started-editor-11" ]

This creates a System Context view, and automatically adds our software system to it.

[ See Image "getting-started-editor-12" ]

To add the user to the view, select it in the list (to the left of the diagram editor), and click the "Update" button.

[ See Image "getting-started-editor-13" ]

Now we can rearrange the elements by clicking and dragging them around the canvas, or by using the toolbar controls. See [Help - Diagram editor](https://structurizr.com/help/diagram-editor) for more details.

[ See Image "getting-started-editor-14" ]

Click the "Relationships" tab (to the left of the diagram editor).

[ See Image "getting-started-editor-15" ]

To add the relationship to the view, select it in the list (to the left of the diagram editor), and click the "Update" button.

[ See Image "getting-started-editor-16" ]

Scroll down to see the element and relationship styles defined in the workspace. See [Help - Notation](https://structurizr.com/help/notation) to read about how to style elements and relationships.

[ See Image "getting-started-editor-17" ]

Click the "+ Element style" button. This will open a modal, where we can choose which tag we'd like to create a style for. Select "Person", and click the "Create" button.

[ See Image "getting-started-editor-18" ]

This opens a second modal, where we can define the properties for the element style. Choose a shape (Person), and set the background and text colours. Then click the "Update" button.

[ See Image "getting-started-editor-19" ]

The style will be immediately reflected in the diagram editor.

[ See Image "getting-started-editor-20" ]

Now repeat the process to create a style for the "Software System" tag.

[ See Image "getting-started-editor-21" ]

Now we can make any final layout tweaks, and save the workspace by clicking the "Save workspace" button.

## 100 Elements

See [README.md](./100/README.md)

The "Elements" view provides a visual representation of the people, software systems, containers and components contained within the software architecture model.

## 200 Relationships

See [README.md](./200/README.md)

The "Relationships" view provides a visual summary of the relationships between all elements in the model. The darker lines indicate more than a single relationship between two elements.

## 300 Decisions

See [README.md](./300/README.md)

The "Decisions" view provides a visual summary of the decision records in the workspace; allowing you to add, edit and delete decision records.

## 400 Views

See [README.md](./400/README.md)

The "Views" view allows you to manage the set of views contained within the software architecture model.

## 500 Styles

See [README.md](./500/README.md)

You can also modify the styles that affect how elements and relationships are rendered in the diagrams. See [Help - Notation](https://structurizr.com/help/notation) for more details on how tagging and styling works.
