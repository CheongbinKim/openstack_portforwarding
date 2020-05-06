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

* Response Body
<pre><code>
{
    "token": {
        "is_domain": false,
        "methods": [
            "password"
        ],
        "roles": [
            {
                "id": "7d551610d0854b4e99f444c51a520974",
                "name": "reader"
            },
            {
                "id": "31f2cf6b88f74ca88f5eee3e2cd4b6ad",
                "name": "member"
            },
            {
                "id": "b76b5306aa2e4d7f959b77e860399b5a",
                "name": "admin"
            }
        ],
        "expires_at": "2020-05-06T04:52:15.000000Z",
        "project": {
            "domain": {
                "id": "default",
                "name": "Default"
            },
            "id": "ff6d5050179744d78ea2791f3a29db3c",
            "name": "admin"
        },
        "catalog": [
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8774/v2.1/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "0debc8214b9f418790916e2988abaecc"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8774/v2.1/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "a2adf1ac2b724cf9ab22888a1fa7a9fb"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8774/v2.1/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "af71fe0c68bd454c84d039ba4cc6520d"
                    }
                ],
                "type": "compute",
                "id": "2d01af11a9284d689ecdda37a4ff5f72",
                "name": "nova"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8776/v3/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "b406e2c354fc4bb5b19ad42b38740558"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8776/v3/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "bab360d61e344b0c89106cd076780f33"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8776/v3/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "c4745009861b4249b6c936b5ce62c258"
                    }
                ],
                "type": "volumev3",
                "id": "3580acbca15d420cabb9639328811252",
                "name": "cinderv3"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8041",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "08152c429b9541d783b780d64756b217"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8041",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "6d098250256f420594bfee532b072fe3"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8041",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "faa6ede4eb694c3cacf1f62c06be74bd"
                    }
                ],
                "type": "metric",
                "id": "56b3a7a51c534741a97e60beede38e7b",
                "name": "gnocchi"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8042",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "67ceb99eb3c1474d8cd3928ebf782837"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8042",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "c10acbb8ad7d4bd3994c7b9ba4a3ce41"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8042",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "e0d857b2d03347da910c5c7579672481"
                    }
                ],
                "type": "alarming",
                "id": "76186ceeceb64d349b87be0ade637d95",
                "name": "aodh"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8777",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "20419325841940139072359ef232dab1"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8777",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "b98676750d68416189149fa2bd8f58c1"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8777",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "f1e70d66868e4abcb2e2bfad07f75f04"
                    }
                ],
                "type": "metering",
                "id": "81d02bb935f9490882698d297b39ad73",
                "name": "ceilometer"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:5000/v3",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "3f7548c586ce4ef2aa1cf43150b54a8f"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:5000/v3",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "8a7ecf22e3084821b137862468e61b19"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:5000/v3",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "c1fed79572f0472da2f1f379042bcb72"
                    }
                ],
                "type": "identity",
                "id": "8517decc5fb64264b33778d7e1a925b1",
                "name": "keystone"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:9696",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "1796c505488a4cb0b5c43def82c43dd4"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:9696",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "7b38dc088b56428ba1cefd419e45c5ac"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:9696",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "fe322396f3b742a090f0dc533571198d"
                    }
                ],
                "type": "network",
                "id": "923511bda8cd4412879c3797e41adf2f",
                "name": "neutron"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8776/v2/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "9902e3adf4b04fcca1bff6abe578e5e2"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8776/v2/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "baabedf1e8ad4847a5d6e2a91004f55f"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8776/v2/ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "ecc72f51be8145cf9c58c1cd29b2b9b5"
                    }
                ],
                "type": "volumev2",
                "id": "b871373532e14aae965613fb40079b4a",
                "name": "cinderv2"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:9292",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "469a727ea9f8406f81426faf3fab7cd3"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:9292",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "78789b26d6ea489b94d8c0b5f8d93a2d"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:9292",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "fab6a5991ba542d486ebcd1adf6544f2"
                    }
                ],
                "type": "image",
                "id": "c8358617b4c2461fb8a3a8bf50e55726",
                "name": "glance"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8080/v1/AUTH_ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "753db5898af147218f0c3bcb7e392350"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8080/v1/AUTH_ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "eed209d5f96b484099a366f34a4d6cc0"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8080/v1/AUTH_ff6d5050179744d78ea2791f3a29db3c",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "f67be138e2ce4b13a07bc719b652e366"
                    }
                ],
                "type": "object-store",
                "id": "f134acce5f3942a5ae08ab8fa96ee935",
                "name": "swift"
            },
            {
                "endpoints": [
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8778/placement",
                        "region": "RegionOne",
                        "interface": "public",
                        "id": "67f648038ec84b8eb43dfc5d0d7b743d"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8778/placement",
                        "region": "RegionOne",
                        "interface": "admin",
                        "id": "a067b81869d0405b96cc3a854b6dcbd2"
                    },
                    {
                        "region_id": "RegionOne",
                        "url": "http://10.254.1.198:8778/placement",
                        "region": "RegionOne",
                        "interface": "internal",
                        "id": "f2bb8d898c694a72b4fae7d757b7d8ae"
                    }
                ],
                "type": "placement",
                "id": "f808a516a6b74ec1ba3c1b796219553d",
                "name": "placement"
            }
        ],
        "user": {
            "password_expires_at": null,
            "domain": {
                "id": "default",
                "name": "Default"
            },
            "id": "eddd37d33288479ab426a6ecaf9cd7c9",
            "name": "admin"
        },
        "audit_ids": [
            "kkxXbLUrQhKldpIqiZTTpA"
        ],
        "issued_at": "2020-05-06T03:52:15.000000Z"
    }
}
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
