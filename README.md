# openstack_portforwarding

[OpenStack Network API](https://docs.openstack.org/api-ref/network/v2/?expanded=create-floating-ip-detail,list-floating-ips-detail,update-a-port-forwarding-detail#floating-ips-port-forwarding, "port-forwarding")

***

# Step 1. Get token

* Request
- URL : 10.254.1.198:5000/v3/auth/tokens
- METHOD : POST
- HEADER : Conent-Type:application/json
- BODY : 
<pre>
<code>
{
	"auth": {
        "identity": {
            "methods": [
                "password"
            ],
            "password": {
                "user": {
                    "name": "admin",
                    "domain": {
                        "name": "Default"
                    },
                    "password": "82d0272d76be41ab"
                }
            }
        },
        "scope": {
            "project": {
                "domain": {
                    "id": "default"
                },
                "name": "admin"
            }
        }
    }
}
</pre>
</code>

* Response Header
<pre><code>
x-subject-token →gAAAAABesjRvRkcdorudhmVpSxD0QgDnu5avZf4KQnP2JTR5c5KW5LIFWTrkn5700mSxOH3fxQMroUhE6hOGfB1ch5w9eTGvQe0NgRrwMCCjT3-OCQPFGNNp8U68nGIkwcE0JfFKr58smi4OXgldk-xp_vjIATOq_PoB2G2v7ryp5tL6Rqk7Tyw
</pre></code>

# Step 2. Get floating-ip
* Request
- URL : 10.254.1.198:9696/v2.0/floatingips
- METHOD : GET
- HEADER : Conent-Type:application/json, x-auth-token:gAAAAABesjRvRkcdorudhmVpSxD0QgDnu5avZf4KQnP2JTR5c5KW5LIFWTrkn5700mSxOH3fxQMroUhE6hOGfB1ch5w9eTGvQe0NgRrwMCCjT3-OCQPFGNNp8U68nGIkwcE0JfFKr58smi4OXgldk-xp_vjIATOq_PoB2G2v7ryp5tL6Rqk7Tyw

* Response
<pre><code>
{
    "floatingips": [
        {
            "router_id": null,
            "status": "DOWN",
            "description": "",
            "tags": [],
            "tenant_id": "ff6d5050179744d78ea2791f3a29db3c",
            "created_at": "2020-05-06T01:20:47Z",
            "updated_at": "2020-05-06T01:20:47Z",
            "floating_network_id": "8f46610a-e6f8-4d13-b709-78337f9b3e1d",
            "port_details": null,
            "fixed_ip_address": null,
            "floating_ip_address": "10.254.1.153",
            "revision_number": 0,
            "project_id": "ff6d5050179744d78ea2791f3a29db3c",
            "port_id": null,
            "id": "3c3c5101-89ff-4c10-9d07-fc192f04855a",
            "qos_policy_id": null
        }
    ]
}
</pre></code>


