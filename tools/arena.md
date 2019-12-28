# Arena

{% api-method method="get" host="https://api.cakes.com" path="/v2/users/:id" %}
{% api-method-summary %}
Get user data
{% endapi-method-summary %}

{% api-method-description %}
Returns a user object
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID or username of the user
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{ "id" : 6607, "slug" : "jonas-johansson" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



