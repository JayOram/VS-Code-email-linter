# VS-Code-email-linter
A repository to help email developers set up VS Code CSS and HTML linters.

## Why?
VS Code's linter is too modern for email code! We use out of date or mso specific CSS and HTML that is flagged in VS Code:

<img width="216" height="21" alt="image" src="https://github.com/user-attachments/assets/8d0b86f7-29d0-4288-8ff8-9d6388a18527" />

You can update the your personal settings at a project or global level to not highlight correct email specific code. 

## Updating the settings.json file

1. Open Command Palette (Ctrl+Shift+P or Cmd+Shift+P)
2. Type "Preferences: Open Settings (JSON)"

## CSS Linting

To add CSS attributes you can add the `css.lint.validProperties` json object and include all of the CSS atributes that are valid for email:

```
"css.lint.validProperties": [
    "mso-hide",
    "mso-table-lspace",
    "mso-table-rspace",
    ...
  ]
```

For a list of CSS attributes curated by the EmailGeek community, checkout the [latest version](/css-lint.json)

## HTML Data and Descriptions

To add HTML attributes and elements there is a two step process. 

1. Add the below to your settings.json:

```
  "html.customData": [
    "./email-html-data.json"
  ]
```

2. Then set up the email-html-data.json file:

```
{
  "version": 1.1,
  "tags": [
    {
      "name": "v:*",
      "description": "Vector Markup Language elements for Outlook",
      "void": false
    },
    {
      "name": "o:*", 
      "description": "Office namespace elements",
      "void": false
    }
  ],
  "globalAttributes": [
    {
      "name": "mso-*",
      "description": "Microsoft Office specific attributes"
    },
    {
      "name": "cellpadding",
      "description": "Table cell padding (deprecated in HTML5 but required for email)"
    },
    {
      "name": "cellspacing",
      "description": "Table cell spacing (deprecated in HTML5 but required for email)"
    },
    ...
    ]
}
```

For a list of HTML elements and attributes curated by the EmailGeek community, checkout the [latest version](/email-html-data.json)

If you would like to add anything to the lists, please open a pull request or add an issue. 

**Inspired by a question asked in the email geeks slack group**

Original idea from:\
[Jay Oram](https://www.linkedin.com/in/jayoram/)\
[Caleb Moore](https://www.linkedin.com/in/calebmoore/)\
[Norman Pribil](https://www.linkedin.com/in/normanpribil/)



