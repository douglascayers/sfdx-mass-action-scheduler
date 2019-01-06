Mass Action Scheduler
=======================

![screen shot](images/wizard-details.png)

Overview
--------

Declaratively schedule Process Builder, Flows, Quick Actions, Email Alerts, Workflow Rules, and Apex to process records from Reports, List Views, and SOQL queries.

* **Declarative** - no code necessary, never write Batch Apex again for queries that can be expressed in a report or list view and actions that can be expressed in a declarative alternative
* **On Platform** - everything happens in Salesforce so no exporting or uploading data
* **Timely** - run actions manually or schedule hourly, daily, weekly, or any time in between

Inspired by Marie Chandra's idea [Ability to Schedule when Process Builder Triggers](https://success.salesforce.com/ideaView?id=08730000000DjEmAAK).

Inspired by Narender Singh's idea [Ability to schedule flows, workflows and processes in process builder](https://success.salesforce.com/ideaView?id=0873A000000EA71QAG).

No more waiting for records to be updated or creating clever workarounds to cause records to be updated to cause these actions to fire.


Documentation and Discussion
--------------------------

* For discussion and feedback [post in the community group](https://success.salesforce.com/_ui/core/chatter/groups/GroupProfilePage?g=0F93A000000LhvN) or raise well defined issues and ideas via the [Issues feature](https://github.com/douglascayers/sfdx-mass-action-scheduler/issues).
* Watch my [Automation Hour webinar](https://youtu.be/XYBKrrXgBxA?list=PL-oxrNbxQl3-Wp8k-z3pa2y_VOw88TMfw) introducing the tool and demos.
* Read the [wiki page](https://github.com/douglascayers/sfdx-mass-action-scheduler/wiki) for further documentation on Mass Action Scheduler.
* Read the [FAQ page](https://github.com/douglascayers/sfdx-mass-action-scheduler/wiki/Frequently-Asked-Questions) to help troubleshoot technical issues.

[![video](images/mass-action-scheduler-youtube-cover.png)](https://youtu.be/XYBKrrXgBxA?list=PL-oxrNbxQl3-Wp8k-z3pa2y_VOw88TMfw)


Data Sources
------------

Identify the records you want to process with list views, tabular reports, or a SOQL query.

| Data Sources      | When to Use |
|-------------------|-------------|
| **List Views**    | Simple filters. For up to 50 million records. |
| **Reports**       | Complex filters like [Cross Filters](https://help.salesforce.com/articleView?id=reports_cross_filters_create.htm&type=5). For up to [~10 thousand records](https://github.com/douglascayers/sfdc-add-campaign-members-by-report/issues/17#issuecomment-332382142). |
| **SOQL**          | You know exactly what you want to query and don't want to create a list view or report. For up to 50 million records. |    


Actions
-------

Almost any process automation you configure can be scheduled.

| Actions               | Supported Types |
|-----------------------|-----------------|
| **Process Builder**   | Processes that start when invoked by another process |
| **Flows**             | Auto-launched flows (no screens). Any that can be called from Process Builder |
| **Quick Actions**     | Create a Record, Update a Record, and Log a Call types |
| **Email Alerts**      | All |
| **Workflow Rules**    | Active rules |
| **Apex**              | Classes annotated with @InvocableMethod |


Scheduling
----------

Flexible options for scheduling when a configuration runs.

| Scheduling Options        | When to Use |
|---------------------------|-------------|
| **Manual**                | Run on-demand from UI via button |
| **Automated**             | Run a configuration from Process Builder, Flow, or Apex |
| **Simple Schedule**       | Easily pick the hours, days, and months to run repeatedly |
| **Advanced Schedule**     | Custom scheduling needs that require a cron expression |


What you can do with Mass Action Scheduler
------------------------------------------

I'm sure you will think of all kinds of ideas how you can use this app. Here are a few ideas:
* Run a process monthly, maybe to create a record or callout to an external system
* Run data correction actions daily
* Automatically add leads and contacts to campaigns based on report or list view criteria
* Send emails on a periodic basis
* Create "infinite" flows that continuously loop on a schedule
* Perform field updates without exporting or importing data

For walkthroughs please check out the [examples in the wiki](https://github.com/douglascayers/sfdx-mass-action-scheduler/wiki/Examples).


Pre-Requisites
--------------

There are a few items you need to setup before installing and using this app.

1. You will need to use [Lightning Experience](https://trailhead.salesforce.com/en/content/learn/modules/lex_migration_introduction) because we are using Lightning Components.
2. You will need to enable [My Domain](https://trailhead.salesforce.com/en/content/learn/modules/identity_login/identity_login_my_domain) because we are using Lightning Components.
3. You will need to disable [Freeze JavaScript Prototypes](https://developer.salesforce.com/docs/atlas.en-us.lightning.meta/lightning/security_freeze_prototypes.htm) because we [share JavaScript code](https://developer.salesforce.com/docs/atlas.en-us.lightning.meta/lightning/security_share_code.htm) using static resources.
    * From Setup, enter `session` in the Quick Find box, then click **Session Settings**.
    * Uncheck **Freeze JavaScript Prototypes** and click **Save**.
    * For a technical explanation on why this is needed, read my [blog post](https://douglascayers.com/2018/12/30/sharing-javascript-code-in-lightning-aura-components-and-freezing-javascript-prototypes/).

Please see the [instructions in the wiki](https://github.com/douglascayers/sfdx-mass-action-scheduler/wiki/Pre-Requisites-Instructions) for screen shots and step-by-steps.


Packaged Release History
========================

Support
-------

Mass Action Scheduler is an open source project. It's an independent project with its ongoing development happening in the evenings and weekends.
Maintaining and developing new features takes a considerable amount of time. If your business has found value in my projects, please consider [showing
your support](https://douglascayers.com/thanks-for-your-support/) by contributing to my [virtual tip jar on PayPal](https://www.paypal.me/douglascayers/). Thank you! ❤️

Release 2.0 (current)
-----------

_Due to Lightning Experience web page caching, please log out and log back in after installing the package for UI changes to appear._

* Install Package ([Production](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tf4000003vWNm)) ([Sandbox](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tf4000003vWNm))
* [Release Notes](https://github.com/douglascayers/sfdx-mass-action-scheduler/wiki/Upgrading-to-Release-2.0)
* [Closed Issues](https://github.com/douglascayers/sfdx-mass-action-scheduler/milestone/5?closed=1)
* [Archived Releases](https://github.com/douglascayers/sfdx-mass-action-scheduler/milestones?state=closed)

---

Installing the Source Code (Developers)
---------------------------------------

This repository is organized using [Salesforce DX](https://trailhead.salesforce.com/en/trails/sfdx_get_started).
You may install the source code from GitHub and make any desired adjustments.
You are responsible for ensuring unit tests meet your org's validation rules and other requirements.

First, clone the repository.

```
git clone https://github.com/douglascayers/sfdx-mass-action-scheduler.git
```

Change directory into the project folder.

```
cd sfdx-mass-action-scheduler
```

Create a new scratch org.

```
sfdx force:org:create -a mas -s -f config/project-scratch-def.json
```

Push the source metadata into your scratch org.

```
sfdx force:source:push
```

Assign the permission set to your user. 

```
sfdx force:user:permset:assign -n Mass_Action_Admin
```

Open the scratch org and enjoy!

```
sfdx force:org:open --path //lightning/o/Mass_Action_Configuration__c/list
```


Credits
=======

[Doug Ayers](https://douglascayers.com) develops and maintains the project.

[Appiphony](http://www.lightningstrike.io) for developing the Strike Wizard component.

[Salesforce Foundation](https://github.com/SalesforceFoundation/CampaignTools) for developing tools for querying Salesforce Reports API.

[Shinichi Tomita](https://jsforce.github.io/) for developing jsforce library for easy use of Salesforce APIs.

[jQuery](https://jquery.com/) for developing jQuery library.

License
=======

The source code is licensed under the [BSD 3-Clause License](LICENSE)
