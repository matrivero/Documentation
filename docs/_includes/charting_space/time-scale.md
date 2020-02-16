<!--------------------------------------------- TITLE AND DEFINITION starts -->

{% assign title = "Time Scale" %}
{% assign definition = site.data.charting_space.time_scale %}
{% assign preposition = "a" %}
{% assign plural = "s" %}

<!--------------------------------------------- TITLE AND DEFINITION ends -->

{% if include.heading != "" %}
{{include.heading}} {{title}}
{% endif %}

{% if include.icon != "no" %} 

{% if include.table == "yes" and include.icon != "no" %}
<table class="definitionTable"><tr><td>
{% endif %}

<img src='images/icons/{{include.icon}}{{ title | downcase | replace: " ", "-" }}.png' />

{% if include.table == "yes" and include.icon != "no" %}
</td><td>
{% endif %}

{% endif %}

{% if include.definition == "bold" %}

<strong>{{ definition }}</strong>

{% else %}

{{ definition }}

{% endif %}

{% if include.table == "yes" and include.icon != "no" %}
</td></tr></table>
{% endif %}

{% if include.more == "yes" and include.content == "more" %}
<details class="detailsCollapsible"><summary class="nobr">Click to learn more about {{ title | downcase }}{{plural}}
</summary>
{% endif %}

{% if include.content != "no" %}

<!--------------------------------------------- CONTENT starts -->

{{include.heading}}### Scale Minimum and Maximum Values

A time scale has a minimum and a maximum value. The minimum value is the value at the left border of the chart. The maximum, is the value at the right border of the chart.

In technical terms, the minimum and maximum scale values are constantly changing as, whenever you pan across the charts, you are directly affecting the minimum and maximum scale values. That said, the actual scale doesn't change when panning across a chart.

{{include.heading}}### Automatic Scale

The system features an automatic adjustment of the scale, which is turned on by default in our shared workspaces. The scale may be automatic in its minimum value, in its maximum value, or both. 

When the scale is automatic in the minimum value, the scale is adjusted so that the chart shows all data from the beginning of the market. Panning the charts under such setting has the effect of compressing and decompressing the data against the left border of the chart.

When the scale is automatic in the maximum value, the scale is adjusted so that the chart shows all data until the end of the market. In such case, panning the charts has the effect of compresssing and decompressing the data against the right border of the chart.

The scale may be automated on either, or both minimum and maximum values at the same time. In the later case, the chart is locked showing the complete market, and panning has no effect.

{% include note.html content="Having the time scale set to automatic by default helps finding the data as soon as it starts being processed the first time you run the Masters bot instances. It is expected that you dissable the automatic time scale feature, as otherwise, it is not possible to pan the charts." %}

{{include.heading}}### Manual Scale

The system features a manual mode. When in manual mode the scale does not change, even if the minimum and maximum values change while panning through a chart. This the natural state of the time scale, as, otherwise, the natural action of panning the chart to go backwards and forwards in time is blocked. 

<!--------------------------------------------- CONTENT ends -->

{% endif %}

{% if include.charts != "" %}

{{include.charts}} Controlling the {{title}} from the Charts

<!--------------------------------------------- CHARTS starts -->

{{include.charts}}# Automatic Scale

To change the automatic scale settings, place the mouse pointer over the corresponding time box, press the <kbd>Shift</kbd> key and slowly scroll the wheel of the mouse. The action cycles through the different possible scale automation settings. Notice a tiny green triangle below and/or above the rate scale icon. 

* A triangle pointing right means that the maximum value of the scale is automatic. 

* A triangle pointing left means that the minimum value of the scale is automatic.

* Both triangles present at the same time means that both minimum and maximum values are automatic.

* No triangle means that both minimum and maximum values are in manual mode.

{{include.charts}}# Manual Scale

When either or both minimum and maximum values are in manual mode, you may adjust the scale to your liking. Place the mouse pointer over the time box and scroll the wheel of the mouse. The scale will increase or decrease accordingly, depending on which values are set to manual.

Notice that, while changing the scale, a number is displayed replacing the actual datetime. This is a reference value of the scale, that may serve for comparison purposes, with scales in other charts.

{% include note.html content="This action has no effect when both minimum and maximum values are set to automatic mode." %}

<!--------------------------------------------- CHARTS ends -->

{% endif %}

{% if include.more == "yes" and include.content != "more" %}
<details class="detailsCollapsible"><summary class="nobr">Click to learn more about {{ title | downcase }}{{plural}}
</summary>
{% endif %}

{% if include.adding != "" %}

{{include.adding}} Adding {{preposition}} {{title}} Node

<!--------------------------------------------- ADDING starts -->

To add a time scale, select *Add Time Scale* on the time machine node menu.

<!--------------------------------------------- ADDING ends -->

{% endif %}

{% if include.configuring != "" %}

{{include.configuring}} Configuring the {{title}}

<!--------------------------------------------- CONFIGURING starts -->

Select *Configure Rate Scale* on the menu to access the configuration.

```json
{
    "fromDate": "2019-05-02T20:07:50.872Z",
    "toDate": "2019-05-22T20:28:21.515Z",
    "autoMinScale": false,
    "autoMaxScale": false
}
```

* ```minValue``` is a date in the Epoch time format that represents the value of the scale at the left border of the chart.

* ```maxValue``` is a date in the Epoch time format that represents the value of the scale at the right border of the chart.

* ```autoMinScale``` sets the mode of the scale for the minimum value; ```true``` sets the value to automatic, ```false``` sets the value to manual. 

* ```autoMaxScale``` sets the mode of the scale for the maximum value; ```true``` sets the value to automatic, ```false``` sets the value to manual. 

{% include note.html content="The ```minValue``` and ```maxValue``` may be entered via the design space and the charts. Both input methods are synchronized and the resulting values are stored in the node." %}

<!--------------------------------------------- CONFIGURING ends -->

{% endif %}

{% if include.more == "yes" %}
</details>
{% endif %}