Whenever a new vhost is created with the renew script the step-1 will be copied and symlinked to nginx, nginx reloads and letsencrypt is called.
After the certificates has been created step-2 will overwrite the copied domain configuration.

step-1 and step-2 is only used when a new vhost is created with renew.
