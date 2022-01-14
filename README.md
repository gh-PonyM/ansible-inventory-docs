# ansible-inventory-docs

Example of how to use ansible facts to create an overwiew of managed hosts. 

## How-To

Ansible is capable of handling different inventories. The example here uses a default inventory as defined in `ansible.cfg` 
using the yaml notation. In this example, `localhost` is assigned to the group *desktops* as an example.  
Run the playbook and see what happens:

	ansible-playbook inventory_docs.yml

An overview `index.md` with a table of all hosts for the inventory is created as well as a `localhost.md` with all the 
details that are available in the facts using a code block for every entry.

Using another inventory is supported and will create another subfolder.

	ansible-playbook -i inventories/other.yml inventory_docs.yml

If you are new to ansible, there are a few techniques and features contained in this example:

## Jinja Templates

- usage of a macro to render a value from the facts
- An example of how to access a nested value, e.g. `facts.date_time.tz` using a string notation `date_time.tz`.
- Controlling indentation in template blocks using `-` in order to render table in markdown correctly
- Intermediate variable definitions in templates using `{% set variable=.... %}`

## Yaml-Syntax

- Re-use of static expressions (`docs_folder: &folder "docs/inventory"`)
