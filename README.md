# Jinja2

# Create a branch

# Install Jinja2 library
pip install jinja2

# Create templates directory
mkdir templates

# Create Jinja2 template in templates directory
# Example template: generate configuration for a network device
touch templates/network_config.j2

```templates/network_config.j2
hostname {{ hostname }}

{% for interface in interfaces %}
interface {{ interface.name }}
 ip address {{ interface.ip_address }}
{% endfor %}

# Create python file in the root

```
# Import Jinja2 into Nornir script
from jinja2 import Environment, FileSystemLoader

# Load Jinja2 template
env = Environment(loader=FileSystemLoader('templates'))
template = env.get_template('network_config.j2')

# Render Jinja2 template with data
data = {
    'hostname': 'router1',
    'interfaces': [
        {'name': 'GigabitEthernet0/0', 'ip_address': '192.0.2.1'},
        {'name': 'GigabitEthernet0/1', 'ip_address': '198.51.100.1'}
    ]
}
output = template.render(data)
```
## Run the code 
