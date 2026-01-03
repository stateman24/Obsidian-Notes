# **{{title}}**

**Created:** {{dateAdded.format("dddd, MMMM Do YYYY, h:mm:ss a")}}
**Tags:**  {% for tagObj in tags %} #{{ tagObj.tag }} {% endfor %}
**Author(s):** {{authors}}
**Link:** {{url}}
____
{% for noteobj in notes %}
- {{ noteobj.note }}
{% endfor %}

____ 
