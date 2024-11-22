---
title: Task Filtering AND Operation in Aspose.Tasks
linktitle: Task Filtering AND Operation in Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Learn how to leverage the class in Aspose.Tasks for .NET to filter project tasks based on multiple conditions. By combining criteria such as summary tasks and non-null attributes.
type: docs
weight: 10
url: /net/master-advanced-features/task-filtering-and-operation/
---
## Introduction

In this tutorial, we will explore how to perform advanced filtering of project tasks in Aspose.Tasks for .NET by utilizing the `Util.And` class. This powerful feature allows developers to filter tasks based on multiple criteria efficiently.

## Prerequisites

Before we begin, ensure you have the following:

1. Basic knowledge of C# programming.
2. Aspose.Tasks for .NET installed. If you haven’t done this yet, you can download it from [this link](https://releases.aspose.com/tasks/net/).
3. An integrated development environment (IDE) like Visual Studio to write and run the code.

## Importing Namespaces

To get started, you need to import the required namespaces into your C# project. This will allow you to access the functionalities provided by Aspose.Tasks.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## Step 1: Initialize the Project and Collect Tasks

First, initialize an Aspose.Tasks project and gather all tasks within it. For demonstration purposes, we’ll assume there’s a project file named `Project2.mpp`.

```csharp
// Path to the documents directory
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Collect all child tasks
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## Step 2: Define Filter Conditions

In this step, we’ll define the conditions for filtering tasks. In our example, we will create two conditions: one to filter for summary tasks and another to ensure that tasks are not null.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## Step 3: Combine Conditions with the AND Operation

The next step is to combine these conditions using the `Util.And` class. This allows us to create a composite condition that mandates both criteria.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## Step 4: Apply the Combined Condition and Filter Tasks

Now, let’s apply the combined condition to the collected tasks to filter out the specific tasks that meet both conditions.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## Step 5: Output the Filtered Tasks

Finally, we will iterate through our filtered tasks and output relevant details. This will help us understand the tasks that meet our criteria.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Conclusion

In this tutorial, we demonstrated how to perform advanced filtering operations in Aspose.Tasks for .NET using the `Util.And` class. By combining multiple conditions, we can effectively filter tasks, thereby enhancing the utility of our project management applications.

## FAQ's

### What is Aspose.Tasks for .NET?

Aspose.Tasks for .NET is a comprehensive API designed for developers to manipulate Microsoft Project files programmatically within .NET applications.

### Can I combine more than two conditions using Util.And?

Yes! The `Util.And` class allows you to combine multiple conditions, enabling complex filtering logic tailored to your needs.

### Is there a free trial version available for Aspose.Tasks?

Yes, you can download a free trial version from [this link](https://releases.aspose.com/).

### Where can I find detailed documentation for Aspose.Tasks?

Detailed documentation is available [here](https://reference.aspose.com/tasks/net/).

### How can I seek support for Aspose.Tasks?

Support is available through the Aspose.Tasks community forum, which can be accessed [here](https://forum.aspose.com/c/tasks/15).
