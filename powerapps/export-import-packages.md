<properties
	pageTitle="Import or export resources | Microsoft Common Data Service"
	description="Import or export resources"
	services="powerapps"
	documentationCenter="na"
	authors="nimakms"
	manager="robinarh"
	editor=""
	tags=""/>

<tags
   ms.service="powerapps"
   ms.devlang="na"
   ms.topic="article"
   ms.tgt_pltfrm="na"
   ms.workload="na"
   ms.date="10/06/2016"
   ms.author=""/>

# Import or export resources
If you've created multiple environments to support the development of your database and apps, you must move changes from one environment to another environment. You can use **Export resources** and **Import resources** to move resources between environments.

## Why use multiple environments?
Each environment contains resources, such as entities, flows, and apps, that you create or modify during the development process. 

Typically, development is done in the same environment that is used by the organization's end users. This environment is known as the default environment. It's relatively easy to manage resource changes in the same environment. The app maker validates the changes to make sure that all critical business processes and applications are functional, and then releases the app.

Sometimes, development and testing are done in separate environments, and changes are moved to the default environment when they are ready to be used by end users. There are several reasons why you might use separate environments. For example, you might have used a separate environment when you initially evaluated the system. Alternatively, you might want to minimize the risk that is involved when changes are made to the default environment. Separate environments provide isolation, because you make your changes in an environment that isn't the default environment. Depending on the extent of the risks, you might create an additional staging environment. In this case, you have a development environment, a staging environment, and a default environment.

## Moving resource changes
You move resources through separate export and import processes, by using a package (.pkg) file.
<!--Either, all resources can be exported as one package, or specific resources would have to be selected for export. In either case a -->

The package file is exported, saved to local storage, sent to the administrator of the target environment, and then imported into the target environment. The import process is often followed by validation testing to help guarantee that no critical business processes have been adversely affected.

The functionality for both resource import and resource export is available in the **Environments** section of the administrator portal. Both export and import occur in the context of a selected environment.

### Export all resources
If you select **All resources** as an option, the export package contains all changes to entities, pick lists, translation sets, permission sets, and roles. This option lets you move all the contents of one environment to another environment.
<!-- This feature will be turned on in subsequent sprints
### Exporting specific resources ###

When specific resources option is selected, the user will get a chance to manually select specific resources, at first from entities, pick lists, and translation sets. During the second step, security resources are automatically selected based on entity selection from previous step, but user will have a chance to manually modify selection.
-->

1. On [admin.powerapps.com](https://admin.powerapps.com), in the left navigation pane, click **Environments**.
1. Select the source environment.
1. In the upper right, click **Export resources**.
1. When you receive an "Export completed" message, save the package file in local storage.

### Import resources

The first step is to select a package file that was exported from the source environment. The import process validates, analyzes, and tries to import the package.
<!-- This feature will light up in later sprints
As part of the import process, if the analysis reveals conflicts, the details of those conflicts are presented to user before the final import step. Some of these conflicts will block the process from completing, and as such these are flagged, and the process will be terminated. Assuming there are no blocking conflicts, detailed information will be provided regarding any non-blocking conflicts, including the related resource information, the type of change being applied, the reason behind the conflict, what will happen as part of import, and next steps if applicable.

As an example, in cases where an entity field is removed, the conflict is handled by keeping the old field and underlying data, and instructing the user to manually delete it if needed.
-->

1. On [admin.powerapps.com](https://admin.powerapps.com), in the navigation pane, click **Environments**.
1. Select the target environment.
1. In the upper right, click **Import resources**.
1. Click **Select**, and browse to a package file in local storage.
1. Click **Import**.

If the package is only partially applied, you receive an error message that describes what was imported and what wasn't imported.

## Resource types
The development process can involve changes to many types of resources. For example, if you update an app, you might add, remove, or update several entities or connections. Changes to most, if not all, resource types can be moved across environments. The following sections describe the types of resources that you can move.

### Entities, pick lists, and translation sets
You can export and import entities, pick lists, and translation sets as follows:

+ **Standard entities** – Customizations are moved across environments. (You can't modify the out-of-box fields of standard entities.)
+ **Custom entities** – Custom entities are moved across environments.
+ **Standard pick lists** – Standard pick lists are moved across environments. (You can't modify the out-of-box fields of standard pick lists.)
+ **Custom pick lists** – Custom pick lists are moved across environments.
+ **Translation sets** – Translation sets are moved across environments. For more information, see [Translation sets](translation-sets.md).

### Permission sets and roles
Permission sets and roles are security resources that help control access to the database. Both can be moved across environments. After you move permission sets and roles, you should make sure that the permission sets are referenced by the appropriate roles, and that the appropriate users are assigned to any new roles. For more information, see [Configure database security](database-security.md).
<!-- This feature will light up in later sprints   -- When going with the option of selecting specific resources, some permission sets may be automatically selected, if the user already selected entities referencing them. Similarly, some roles may be automatically selected, if any contained permission sets are already selected. User will be able to manually modify selection. -->
<!--
### Other resources coming soon
Over time, resource export functionality will support most if not all of the resources used within CDM, Power Apps and Flow. These will include but will not be limited to resources like Connections, Flows and Apps.
-->

## Data
You can't move database data as part of the export and import of resources. To move data, you can use Microsoft Excel. For more information, see [Import or export data](data-platform-export-data.md).
<!-- ## Migrating from Public Preview ##
For the limited number of users who signed up for our Public Preview, given that their environments will not be upgraded to the latest version, documentation will be provided, in order to enable moving resources and data from the old environment to a new one. Please refer to [Public Preview to GA Migration Topic]
-->