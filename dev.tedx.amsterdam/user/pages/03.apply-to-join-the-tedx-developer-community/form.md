---
title: 'Apply to join the TEDX developer community'
form:
    name: application-form
    fields:
        -
            name: name
            label: Name
            placeholder: 'Enter your name'
            autofocus: 'on'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: email
            label: Email
            placeholder: 'Enter your email address'
            type: email
            validate:
                required: true
        -
            name: github
            label: Github
            placeholder: 'Enter your github profile url'
            type: text
    buttons:
        -
            type: submit
            value: Submit
        -
            type: reset
            value: Reset
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.from }}', '{{ form.value.email }}']
                subject: '[Feedback] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: apply-
                dateformat: Ymd-His-u
                extension: txt
                body: Thanks
        -
            message: 'Thank you for your application!'
        -
            display: thank-you
---

> Apply to join the TEDX developer community