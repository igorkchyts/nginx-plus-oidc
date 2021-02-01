# nginx-plus-oidc
Add nginx-plus proxy with Keycloak Single Sign-on 

# Instructions:
1. Deploy the following configuration files in your project, modify if required: 
   $ service.yaml; nginx-plus-sa.yaml; nginx-cm.yaml;
2. If you are using DNS server other than 8.8.8.8 look in oidc-conf-cm.yaml for 'resolver' and modify to correct DNS server.
   Deploy 'oidc-conf-cm.yaml' to your cluster 
3. Configure frontend-cm.yaml. This configmap holds frontend.conf which holds the OIDC configuration for SSO and your backend application route.
   a. Edit your backend service address
   b. Edit your OIDC configurations
   c. Configure the headers to proxy to the backend application by changing 'proxy_set_header' accordingly
   Deploy 'frontend-cm.yaml' to your cluster
4. Edit 'deployment.yaml' with accessible and licensed NGINX Plus Image and deploy to your cluster
5. Expose NGINX Plus service using your prefered Ingress
6. Include new NGINX public URL in your Keycloak client settings 'Valid Redirect URLs' 
   Format: http://my-nginx.example.com:8010/_codexch
   Notes:
   - For production, we strongly recommend that you use SSL/TLS (port 443).
   - The port number is mandatory even when you’re using the default port for HTTP (80) or HTTPS (443).
7. Test access to your application
