{% if channel != "production" %}
Don't forget to turn on auto-updates in TestFlight to always get the latest builds.

{% endif %}
{% for category, changes in release.changes -%}
{%- for change in changes -%}
{% if change.commitHash|attrs:"Release-Notes" %}
- {{ change.commitHash|attrs:"Release-Notes" }}
{% endif %}
{%- endfor -%}
{%- endfor %}
- Bug fixes and stability improvements
