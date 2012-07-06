---
title:Kendo.Mvc.UI.Fluent.ChartAxisLabelsDateFormatsBuilder
slug:aspnetmvc-kendo.mvc.ui.fluent.chartaxislabelsdateformatsbuilder
publish:true
---

# Kendo.Mvc.UI.Fluent.ChartAxisLabelsDateFormatsBuilder

## Methods

### Months(System.String)
Sets the date format when the base date unit is

#### Example
    <%= Html.Kendo().Chart()
        .Name("Chart")
        .CategoryAxis(axis => axis
        .Date()
        .Labels(labels => labels
        .DateFormats(formats => formats
        .Months("HH:mm")
        )
        )
        );
        %>

#### Parameters

##### format `System.String`
The date format.