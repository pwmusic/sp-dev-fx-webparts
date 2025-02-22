---
page_type: sample
products:
- office-sp
languages:
- javascript
- typescript
extensions:
  contentType: samples
  technologies:
  - SharePoint Framework
  platforms:
  - react
  createdDate: 3/1/2017 12:00:00 AM
---
# Script editor web part for modern pages built in React

This version is built on SPFx v1.4.1. The version works for both SharePoint Online and for SharePoint on-premises.

The SPO only version can be found at [react-script-editor](../react-script-editor) and it is similar in functionality but has an improved editor experience.

## Summary
Coming from old classic SharePoint pages you might have existing script solutions you want to re-use on a modern page
without having to repackage it as a new SharePoint Framework web part. This web part is similar to the classic
Script Editor Web Part, and allows you do drop arbitrary script or html on a modern page.

> Notice. All client-side web parts are deployed or enabled to be available in site level by tenant administrator using tenant app catalog. If there are concerns on enabling script options in a tenant, this web part or a approach should not be approved by tenant administrators.

As an example add the following scripts to the web part in order to show stock ticker info on your page. First *tv.js* is loaded, and then the script block is executed to show the ticker information.

```html
<!-- TradingView Widget BEGIN -->
<div class="tradingview-widget-container">
  <div id="tradingview_e7aa0"></div>
  <div class="tradingview-widget-copyright"><a href="https://www.tradingview.com/symbols/NASDAQ-AAPL/" rel="noopener" target="_blank"><span class="blue-text">AAPL Chart</span></a> by TradingView</div>
  <script type="text/javascript" src="https://s3.tradingview.com/tv.js"></script>
  <script type="text/javascript">
  new TradingView.widget(
  {
  "width": 980,
  "height": 610,
  "symbol": "NASDAQ:AAPL",
  "interval": "D",
  "timezone": "Etc/UTC",
  "theme": "light",
  "style": "1",
  "locale": "en",
  "toolbar_bg": "#f1f3f6",
  "enable_publishing": false,
  "allow_symbol_change": true,
  "container_id": "tradingview_e7aa0"
}
  );
  </script>
</div>
<!-- TradingView Widget END -->
```

The web part works by loading each script in a `<script src>` tag sequentially in the order they are specified, then any other `<script>` block is executed.

![Script Editor web part](./assets/modern-script-editor-wp.gif)

If all you want is to add markup on the page, you can do that as well. Adding the following html would show a headline and a list.

```html
<h2>My header</h2>
<ul>
    <li>One
    <li>Two
    <li>Three
</ul>
```

You may add CSS via style tags or `link` tags.
```html
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<style>
    #container h1 {
        color: red;
    }
</style>
<div id="container">
    <h1>Headline</h1>
</div>
<div class="row">
    <div class="col-md-8">.col-md-8</div>
    <div class="col-md-4">.col-md-4</div>
</div>
<div class="row">
    <div class="col-md-4">.col-md-4</div>
    <div class="col-md-4">.col-md-4</div>
    <div class="col-md-4">.col-md-4</div>
</div>
```

## Support for classic _spPageContextInfo
If your scripts rely on the classic _spPageContextInfo, you can enable that in the web part property pane.


# Compatibility

![SPFx 1.4.1](https://img.shields.io/badge/SPFx-1.4.1-green.svg) 
![Node.js v8 | v6](https://img.shields.io/badge/Node.js-v8%20%7C%20v6-green.svg) 
![Compatible with SharePoint Online](https://img.shields.io/badge/SharePoint%20Online-Compatible-green.svg)
![Compatible with SharePoint 2019](https://img.shields.io/badge/SharePoint%20Server%202019-Compatible-green.svg)
![Does not work with SharePoint 2016 (Feature Pack 2)](https://img.shields.io/badge/SharePoint%20Server%202016%20(Feature%20Pack%202)-Incompatible-red.svg "SharePoint Server 2016 Feature Pack 2 requires SPFx 1.1")
![Local Workbench Compatible](https://img.shields.io/badge/Local%20Workbench-Compatible-green.svg)
![Hosted Workbench Compatible](https://img.shields.io/badge/Hosted%20Workbench-Compatible-green.svg)

## Applies to

* [SharePoint Framework Release GA](https://blogs.office.com/2017/02/23/sharepoint-framework-reaches-general-availability-build-and-deploy-engaging-web-parts-today/)
* [Office 365 tenant](https://docs.microsoft.com/sharepoint/dev/spfx/set-up-your-development-environment)

## Solution

Solution|Author(s)
--------|---------
react-script-editor-onprem | [Mikael Svenson](https://github.com/wobba) ([@mikaelsvenson](http://www.twitter.com/mikaelsvenson), [techmikael.com](techmikael.com))

## Version history

Version|Date|Comments
-------|----|--------
1.0|March 10th, 2017|Initial release
1.0.0.1|August 8th, 2017|Updated SPFx version and CSS loading
1.0.0.2|October 4th, 2017|Updated SPFx version, bundle Office UI Fabric and CSS in webpart
1.0.0.3|January 10th, 2018|Updated SPFx version, added remove padding property and refactoring
1.0.0.4|February 14th, 2018|Added title property for edit mode and documentation for enabling the web part on Group sites / tenant wide
1.0.0.5|March 8th, 2018|Added support for loading scripts which are AMD/UMD modules. Added support for classic _spPageContextInfo. Refactoring.
1.0.0.6|March 26th, 2018|Fixed so that AMD modules don't detect `define`, and load as non-modules.
1.0.0.7|May 23rd, 2018|Added supportsFullBleed to manifest.
1.0.0.8|May 23rd, 2018|Updated SPFx to v1.5.1, made editor load dynamically to reduce runtime bundle size, fixed white space issue.
1.0.0.9|Aug 22, 2018|Improved bundle size
1.0.0.10|Jan 16th, 2019|Fix for removing of web part padding
1.0.0.11|March 18th, 2019|Fix for re-loading of script on smart navigation
1.0.0.12|April 15th, 2019|Re-fix for pad removal of web part
1.0.0.13|July 1th, 2019|Downgrade to SPFx v1.4.1 to support SP2019
1.0.0.14|Oct 13th, 2019|Added resolve to fix pnpm issue. Updated author info.
1.0.0.15|Mar 16th, 2020|Renamed package file. Linked to SPO only version.

## Minimal Path to Awesome

### Local testing

- Clone this repository
- In the command line run:
  - `npm install`
  - `gulp serve`

### Deploy
* gulp clean
* gulp bundle --ship
* gulp package-solution --ship
* Upload .sppkg file from sharepoint\solution to your tenant App Catalog or to your on-premises app catalog.
	* E.g.: https://&lt;tenant&gt;.sharepoint.com/sites/AppCatalog/AppCatalog or https://myserver/sites/apps
* Add the web part to a site collection, and test it on a page

### Deploy to non-script sites / modern team sites
By default this web part is not allowed on no-script sites, as it allows execution of arbitrary script. This is by design as from a security and governance perspective you might not want arbitrary script added to your pages. This is typically something you want control over.

If you however want to allow the web part for non-script sites like Office 365 Group modern team sites you have to edit `ScriptEditorWebPart.manifest.json` with the following change:
```
"requiresCustomScript": false
```

### Deploy tenant wide
By default you have to install this web part per site collection where you want it available. If you want it enabled by default on all sites you have to edit `package-solution.json` with the following change:
```
"skipFeatureDeployment": true
```

In order to make it available to absolutely all sites you need apply the _Deploy to non-script sites / modern team site_ change as well.

## Features
This web part illustrates the following concepts on top of the SharePoint Framework:

- Re-use existing JavaScript solutions on a modern page
- Office UI Fabric
- React

## Help

We do not support samples, but this community is always willing to help, and we want to improve these samples. We use GitHub to track issues, which makes it easy for  community members to volunteer their time and help resolve issues.

If you're having issues building the solution, please run [spfx doctor](https://pnp.github.io/cli-microsoft365/cmd/spfx/spfx-doctor/) from within the solution folder to diagnose incompatibility issues with your environment.

You can try looking at [issues related to this sample](https://github.com/pnp/sp-dev-fx-webparts/issues?q=label%3A%22sample%3A%20react-script-editor%22) to see if anybody else is having the same issues.

You can also try looking at [discussions related to this sample](https://github.com/pnp/sp-dev-fx-webparts/discussions?discussions_q=react-script-editor) and see what the community is saying.

If you encounter any issues while using this sample, [create a new issue](https://github.com/pnp/sp-dev-fx-webparts/issues/new?assignees=&labels=Needs%3A+Triage+%3Amag%3A%2Ctype%3Abug-suspected%2Csample%3A%20react-script-editor&template=bug-report.yml&sample=react-script-editor&authors=@wobba&title=react-script-editor%20-%20).

For questions regarding this sample, [create a new question](https://github.com/pnp/sp-dev-fx-webparts/issues/new?assignees=&labels=Needs%3A+Triage+%3Amag%3A%2Ctype%3Aquestion%2Csample%3A%20react-script-editor&template=question.yml&sample=react-script-editor&authors=@wobba&title=react-script-editor%20-%20).

Finally, if you have an idea for improvement, [make a suggestion](https://github.com/pnp/sp-dev-fx-webparts/issues/new?assignees=&labels=Needs%3A+Triage+%3Amag%3A%2Ctype%3Aenhancement%2Csample%3A%20react-script-editor&template=suggestion.yml&sample=react-script-editor&authors=@wobba&title=react-script-editor%20-%20).


## Disclaimer

**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**

<img src="https://telemetry.sharepointpnp.com/sp-dev-fx-webparts/samples/react-script-editor" />
