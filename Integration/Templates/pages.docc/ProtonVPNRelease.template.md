# ProtonVPN Release: {{ release.versionString }} ({%- include "timestamp" -%})
@Metadata {
    @TechnologyRoot
}
{% if release.body %}
## Release Notes

{{ release.body }}
{% endif %}
## Changes
{% for category, changes in release.changes +%}

### {{ config.changelogTypeDisplayNames[category]|default:category }}
{% for change in changes %}
- `{{ change.commitHash|prefix:oidStringLength }}` {%+ if change.scope %}{{ change.scope }}: {%+ endif %}{{ change.summary }}{% if change.projectIds +%} ({% for projectId in change.projectIds %}[{{ projectId }}]({{ config.userProperties.jiraIssueBaseURL }}/{{ projectId }}){% if not forloop.last %}, {% endif %}{% endfor %}){% endif +%}
{% endfor %}
{% endfor %}

{% if checklist_filenames %}
## Topics
### Checklists
{% for filename in checklistFilenames %}
- <article:{{ filename }}>
{% endfor %}
{% endif %}
