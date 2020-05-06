# openstack_portforwarding

[OpenStack Network API](https://docs.openstack.org/api-ref/network/v2/?expanded=create-floating-ip-detail,list-floating-ips-detail,update-a-port-forwarding-detail#floating-ips-port-forwarding, "port-forwarding")

***

# 1. Get token

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

* Response
<pre><code>
x-subject-token →gAAAAABesjRvRkcdorudhmVpSxD0QgDnu5avZf4KQnP2JTR5c5KW5LIFWTrkn5700mSxOH3fxQMroUhE6hOGfB1ch5w9eTGvQe0NgRrwMCCjT3-OCQPFGNNp8U68nGIkwcE0JfFKr58smi4OXgldk-xp_vjIATOq_PoB2G2v7ryp5tL6Rqk7Tyw
</pre></code>
