{% if channel == "alpha" %}
Internal alpha release. Latest changes:

{% elif train == "iOS" and channel == "beta" %}
Don't forget to turn on auto-updates in TestFlight to always get the latest builds.

Latest changes in {{ version }}:
{% endif %}
{% for category, changes in release.changes -%}
{%- for change in changes -%}
{% if change.commitHash|attrs:config.trailers.releaseNotes %}
- {{ change.commitHash|attrs:config.trailers.releaseNotes }}
{% elif change.commitHash|attrs:"Release-Notes" %}
- {{ change.commitHash|attrs:"Release-Notes" }}
{% endif %}
{%- endfor -%}
{%- endfor %}
- Bug fixes and stability improvements
