### Pihole Deployments

This repository contains the deployments of Pihole on kubernetes cluster in Raspberry Pi.

In `deployment.yml` file you need to configure your primary and secondary `dns`. Primary DNS needs to be your cluster DNS and you need to change it according to your cluster's configuration.

## Managing Password

This deployment gets password from `secret.yml` file. This secret will be consume inside container as an environmental variable and accoriding to [kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/secret/) you need to encode it with `base64`:

```
echo -n '9LbpGm*4jmCiKvTmL' | base64
```

In above example my password is `9LbpGm*4jmCiKvTmL` but the outcoume which I added in `secret.yml` is `OUxicEdtKjRqbUNpS3ZUbUw=` .

***
# Note:

If you configure the secret through a manifest (JSON or YAML) file which has the secret data encoded as base64, sharing this file or checking it in to a source repository means the secret is compromised. Base64 encoding is not an encryption method and is considered the same as plain text. [Reference](https://kubernetes.io/docs/concepts/configuration/secret/)

***
# Recommendation:

If you need to share the file in a public repository, I would recommend encrypting the `secret.yml` file by using [git-crypt](https://github.com/AGWA/git-crypt)
