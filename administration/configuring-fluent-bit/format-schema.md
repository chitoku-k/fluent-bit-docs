# Formats and Schema

Fluent Bit might optionally use a configuration file to define how the service will behave. Starting in Fluent Bit 1.9, it supports yaml format plus the usual plain text.

Before proceeding we need to understand how the configuration schema works.

The schema is defined by three concepts:

* Sections
* Entries: Key/Value
* Indented Configuration Mode

A simple example of a configuration file is as follows:

{% tabs %}
{% tab title="fluent-bit.conf" %}

```python
[SERVICE]
    # This is a commented line
    Daemon    off
    log_level debug
```
{% endtab %}

{% tab title="fluent-bit.yaml" %}
```yaml
service:
    # This is a commented line
    daemon: off
    log_level: debug
```
{% endtab %}
{% endtabs %}

## Sections <a id="sections"></a>

A section is defined by a name or title inside brackets. Looking at the example above, a Service section has been set using **\[SERVICE\]** definition. Section rules:

* All section content must be indented \(4 spaces ideally\).
* Multiple sections can exist on the same file.
* A section is expected to have comments and entries, it cannot be empty.
* Any commented line under a section, must be indented too.

## Entries: Key/Value <a id="entries_kv"></a>

A section may contain **Entries**, an entry is defined by a line of text that contains a **Key** and a **Value**, using the above example, the `[SERVICE]` section contains two entries, one is the key **Daemon** with value **off** and the other is the key **Log\_Level** with the value **debug**. Entries rules:

* An entry is defined by a key and a value.
* A key must be indented.
* A key must contain a value which ends in the breakline.
* Multiple keys with the same name can exist.

Also commented lines are set prefixing the **\#** character, those lines are not processed but they must be indented too.

## Indented Configuration Mode <a id="indented_mode"></a>

Fluent Bit configuration files are based in a strict **Indented Mode**, that means that each configuration file must follow the same pattern of alignment from left to right when writing text. By default an indentation level of four spaces from left to right is suggested. Example:

{% tabs %}
{% tab title="fluent-bit.conf" %}
```python
[FIRST_SECTION]
    # This is a commented line
    Key1  some value
    Key2  another value
    # more comments

[SECOND_SECTION]
    KeyN  3.14
```
{% endtab %}
{% tab title="fluent-bit.yaml" %}
```yaml
first_section:
    # This is a commented line
    Key1: some value
    Key2: another value
    # more comments

second_section:
    KeyN: 3.14
```
{% endtab %}
{% endtabs %}

As you can see there are two sections with multiple entries and comments, note also that empty lines are allowed and they do not need to be indented.

