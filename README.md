# Ansible role for installing scheduled restic backup jobs

This role depends on the [ansiblization/syslog](https://github.com/ansiblization/syslog) role for logging capabilities.

The restic jobs to be scheduled have to be defined as a list named `restic_jobs`:

```yml
restic_jobs: [{restic_vars}, ...]
restic_vars:
    name: "{{ restic_job.name }}"
    paths: "{{ restic_job.paths }}"
    password: "{{ restic_job.password }}"
    repository: "{{ restic_job.repository }}"
    compression: "{{ restic_job.compression | default('auto') }}"
    schedule: "{{ restic_job.schedule | default(None) }}"
    exclude: "{{ restic_job.exclude | default([]) }}"
    environment: "{{ restic_job.environment | default({}) }}"
    conflicts: "{{ restic_job.conflicts | default([]) }}"
    state: "{{ restic_job.state | default('present') }}"
    prune: "{{ restic_job.prune | default(true) }}"
    keep_hourly: "{{ restic_job.keep_daily | default(24) }}"
    keep_daily: "{{ restic_job.keep_daily | default(7) }}"
    keep_weekly: "{{ restic_job.keep_weekly | default(4) }}"
    keep_monthly: "{{ restic_job.keep_monthly | default(6) }}"
    keep_yearly: "{{ restic_job.keep_monthly | default(4) }}"
```
