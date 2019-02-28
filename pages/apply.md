---
title: Apply
permalink: /apply/
layout: secondary-narrow
timeline:
  - title: anytime
    steps:
      - step-1
      - step-2
      - step-3
  - title: at least 45 days<br> (six weeks) prior<br> to the end of the<br> submission window
    steps:
      - step-4
  - title: upon invitation
    steps:
      - step-5
      - step-6
      - step-7
  - title: Another submission window will open on June 14. 
  - title: 1-3 months after<br> the window closes
    description: Applications undergo panel and merit reviews.
    inactive_description: Applications undergo panel and merit reviews.
  - title: 4-6 months after<br> the window closes
    description: We'll notify you whether your proposal is accepted or declined.
    inactive_description: We'll notify you whether your proposal is accepted or declined.
  - title: 5-6 months after<br> the window closes
    description: If your proposal is accepted, you'll receive funding of up to $225,000.
    inactive_description: If your proposal is accepted, you'll receive funding of up to $225,000.
---
<head>
<script type="text/javascript">
setTimeout(function(){var a=document.createElement("script");
var b=document.getElementsByTagName("script")[0];
a.src=document.location.protocol+"//script.crazyegg.com/pages/scripts/0041/5508.js?"+Math.floor(new Date().getTime()/3600000);
a.async=true;a.type="text/javascript";b.parentNode.insertBefore(a,b)}, 1);
</script>
</head>
<h1 class="page-title">How to apply</h1>

<p class="text-medium">
Learn about our recommended Phase I application timeline, how to prepare your proposal, and what to expect once you submit.
{% if site.app_process == "inactive" %}
Details for the next {{ site.deadline }} deadline will be posted in {{ site.solicitation_released }} in the upcoming solicitations.
{% endif %}
</p>

<ol class="timeline {% if site.app_process == "inactive" %} timeline-inactive {% endif %}">
{% assign step_counter = 1 %}
{% for milestone in page.timeline %}
  <li class="timeline-step{% if milestone.deadline %} timeline-step-deadline{% endif %}">
    {% if site.app_process == "active" %}
      {% assign milestone_description = milestone.description %}
      {% assign milestone_note = milestone.note %}
    {% else %}
      {% assign milestone_description = milestone.inactive_description %}
      {% assign milestone_note = milestone.inactive_note %}
    {% endif %}

    <span class="time">{{ milestone.title }}</span>
    <span class="time-description">
      {{ milestone_description }}
      {% if milestone_note %}<small>{{ milestone_note }}</small>{% endif %}
    </span>

    {% if milestone.steps %}
    <ol class="usa-accordion">
      {% for step in milestone.steps %}
      {% assign timeline_item_ = site.timeline | where:"slug", step %}
      <li value="{{ step_counter }}" class="step {{ step }} {% if site.app_process == "inactive" and timeline_item_[0].becomes_inactive == true %} step-inactive {% endif %}">
        {% include components/accordion-item.html slug=step %}
      </li>
      {% assign step_counter = step_counter | plus: 1 %}
      {% endfor %}
    </ol>
    {% endif %}
  </li>
{% endfor %}
</ol>
