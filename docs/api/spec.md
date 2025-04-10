<p>Packages:</p>
<ul>
<li>
<a href="#external-secrets.io%2fv1beta1">external-secrets.io/v1beta1</a>
</li>
</ul>
<h2 id="external-secrets.io/v1beta1">external-secrets.io/v1beta1</h2>
<p>
<p>Package v1beta1 contains resources for external-secrets</p>
</p>
Resource Types:
<ul></ul>
<h3 id="external-secrets.io/v1beta1.AWSAuth">AWSAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AWSProvider">AWSProvider</a>)
</p>
<p>
<p>AWSAuth tells the controller how to do authentication with aws.
Only one of secretRef or jwt can be specified.
if none is specified the controller will load credentials using the aws sdk defaults.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AWSAuthSecretRef">
AWSAuthSecretRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>jwt</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AWSJWTAuth">
AWSJWTAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AWSAuthSecretRef">AWSAuthSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AWSAuth">AWSAuth</a>)
</p>
<p>
<p>AWSAuthSecretRef holds secret references for AWS credentials
both AccessKeyID and SecretAccessKey must be defined in order to properly authenticate.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>accessKeyIDSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The AccessKeyID is used for authentication</p>
</td>
</tr>
<tr>
<td>
<code>secretAccessKeySecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The SecretAccessKey is used for authentication</p>
</td>
</tr>
<tr>
<td>
<code>sessionTokenSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The SessionToken used for authentication
This must be defined if AccessKeyID and SecretAccessKey are temporary credentials
see: <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html">https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html</a></p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AWSJWTAuth">AWSJWTAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AWSAuth">AWSAuth</a>)
</p>
<p>
<p>Authenticate against AWS using service account tokens.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>serviceAccountRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#ServiceAccountSelector">
External Secrets meta/v1.ServiceAccountSelector
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AWSProvider">AWSProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>AWSProvider configures a store to sync secrets with AWS.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>service</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AWSServiceType">
AWSServiceType
</a>
</em>
</td>
<td>
<p>Service defines which service should be used to fetch the secrets</p>
</td>
</tr>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AWSAuth">
AWSAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Auth defines the information necessary to authenticate against AWS
if not set aws sdk will infer credentials from your environment
see: <a href="https://docs.aws.amazon.com/sdk-for-go/v1/developer-guide/configuring-sdk.html#specifying-credentials">https://docs.aws.amazon.com/sdk-for-go/v1/developer-guide/configuring-sdk.html#specifying-credentials</a></p>
</td>
</tr>
<tr>
<td>
<code>role</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Role is a Role ARN which the SecretManager provider will assume</p>
</td>
</tr>
<tr>
<td>
<code>region</code></br>
<em>
string
</em>
</td>
<td>
<p>AWS Region to be used for the provider</p>
</td>
</tr>
<tr>
<td>
<code>additionalRoles</code></br>
<em>
[]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>AdditionalRoles is a chained list of Role ARNs which the SecretManager provider will sequentially assume before assuming Role</p>
</td>
</tr>
<tr>
<td>
<code>externalID</code></br>
<em>
string
</em>
</td>
<td>
<p>AWS External ID set on assumed IAM roles</p>
</td>
</tr>
<tr>
<td>
<code>sessionTags</code></br>
<em>
<a href="#external-secrets.io/v1beta1.*github.com/external-secrets/external-secrets/apis/externalsecrets/v1beta1.Tag">
[]*github.com/external-secrets/external-secrets/apis/externalsecrets/v1beta1.Tag
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>AWS STS assume role session tags</p>
</td>
</tr>
<tr>
<td>
<code>transitiveTagKeys</code></br>
<em>
[]*string
</em>
</td>
<td>
<em>(Optional)</em>
<p>AWS STS assume role transitive session tags. Required when multiple rules are used with SecretStore</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AWSServiceType">AWSServiceType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AWSProvider">AWSProvider</a>)
</p>
<p>
<p>AWSServiceType is a enum that defines the service/API that is used to fetch the secrets.</p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;ParameterStore&#34;</p></td>
<td><p>AWSServiceParameterStore is the AWS SystemsManager ParameterStore.
see: <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html">https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html</a></p>
</td>
</tr><tr><td><p>&#34;SecretsManager&#34;</p></td>
<td><p>AWSServiceSecretsManager is the AWS SecretsManager.
see: <a href="https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html">https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html</a></p>
</td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AkeylessAuth">AkeylessAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AkeylessProvider">AkeylessProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AkeylessAuthSecretRef">
AkeylessAuthSecretRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Reference to a Secret that contains the details
to authenticate with Akeyless.</p>
</td>
</tr>
<tr>
<td>
<code>kubernetesAuth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AkeylessKubernetesAuth">
AkeylessKubernetesAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Kubernetes authenticates with Akeyless by passing the ServiceAccount
token stored in the named Secret resource.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AkeylessAuthSecretRef">AkeylessAuthSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AkeylessAuth">AkeylessAuth</a>)
</p>
<p>
<p>AkeylessAuthSecretRef
AKEYLESS_ACCESS_TYPE_PARAM: AZURE_OBJ_ID OR GCP_AUDIENCE OR ACCESS_KEY OR KUB_CONFIG_NAME.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>accessID</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The SecretAccessID is used for authentication</p>
</td>
</tr>
<tr>
<td>
<code>accessType</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>accessTypeParam</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AkeylessKubernetesAuth">AkeylessKubernetesAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AkeylessAuth">AkeylessAuth</a>)
</p>
<p>
<p>Authenticate with Kubernetes ServiceAccount token stored.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>accessID</code></br>
<em>
string
</em>
</td>
<td>
<p>the Akeyless Kubernetes auth-method access-id</p>
</td>
</tr>
<tr>
<td>
<code>k8sConfName</code></br>
<em>
string
</em>
</td>
<td>
<p>Kubernetes-auth configuration name in Akeyless-Gateway</p>
</td>
</tr>
<tr>
<td>
<code>serviceAccountRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#ServiceAccountSelector">
External Secrets meta/v1.ServiceAccountSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional service account field containing the name of a kubernetes ServiceAccount.
If the service account is specified, the service account secret token JWT will be used
for authenticating with Akeyless. If the service account selector is not supplied,
the secretRef will be used instead.</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional secret field containing a Kubernetes ServiceAccount JWT used
for authenticating with Akeyless. If a name is specified without a key,
<code>token</code> is the default. If one is not specified, the one bound to
the controller will be used.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AkeylessProvider">AkeylessProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>AkeylessProvider Configures an store to sync secrets using Akeyless KV.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>akeylessGWApiURL</code></br>
<em>
string
</em>
</td>
<td>
<p>Akeyless GW API Url from which the secrets to be fetched from.</p>
</td>
</tr>
<tr>
<td>
<code>authSecretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AkeylessAuth">
AkeylessAuth
</a>
</em>
</td>
<td>
<p>Auth configures how the operator authenticates with Akeyless.</p>
</td>
</tr>
<tr>
<td>
<code>caBundle</code></br>
<em>
[]byte
</em>
</td>
<td>
<em>(Optional)</em>
<p>PEM/base64 encoded CA bundle used to validate Akeyless Gateway certificate. Only used
if the AkeylessGWApiURL URL is using HTTPS protocol. If not set the system root certificates
are used to validate the TLS connection.</p>
</td>
</tr>
<tr>
<td>
<code>caProvider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.CAProvider">
CAProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The provider for the CA bundle to use to validate Akeyless Gateway certificate.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AlibabaAuth">AlibabaAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AlibabaProvider">AlibabaProvider</a>)
</p>
<p>
<p>AlibabaAuth contains a secretRef for credentials.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AlibabaAuthSecretRef">
AlibabaAuthSecretRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>rrsa</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AlibabaRRSAAuth">
AlibabaRRSAAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AlibabaAuthSecretRef">AlibabaAuthSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AlibabaAuth">AlibabaAuth</a>)
</p>
<p>
<p>AlibabaAuthSecretRef holds secret references for Alibaba credentials.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>accessKeyIDSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The AccessKeyID is used for authentication</p>
</td>
</tr>
<tr>
<td>
<code>accessKeySecretSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The AccessKeySecret is used for authentication</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AlibabaProvider">AlibabaProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>AlibabaProvider configures a store to sync secrets using the Alibaba Secret Manager provider.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AlibabaAuth">
AlibabaAuth
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>regionID</code></br>
<em>
string
</em>
</td>
<td>
<p>Alibaba Region to be used for the provider</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AlibabaRRSAAuth">AlibabaRRSAAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AlibabaAuth">AlibabaAuth</a>)
</p>
<p>
<p>Authenticate against Alibaba using RRSA.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>oidcProviderArn</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>oidcTokenFilePath</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>roleArn</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>sessionName</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AzureAuthType">AzureAuthType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AzureKVProvider">AzureKVProvider</a>)
</p>
<p>
<p>AuthType describes how to authenticate to the Azure Keyvault
Only one of the following auth types may be specified.
If none of the following auth type is specified, the default one
is ServicePrincipal.</p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;ManagedIdentity&#34;</p></td>
<td><p>Using Managed Identity to authenticate. Used with aad-pod-identity installed in the cluster.</p>
</td>
</tr><tr><td><p>&#34;ServicePrincipal&#34;</p></td>
<td><p>Using service principal to authenticate, which needs a tenantId, a clientId and a clientSecret.</p>
</td>
</tr><tr><td><p>&#34;WorkloadIdentity&#34;</p></td>
<td><p>Using Workload Identity service accounts to authenticate.</p>
</td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AzureEnvironmentType">AzureEnvironmentType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AzureKVProvider">AzureKVProvider</a>)
</p>
<p>
<p>AzureEnvironmentType specifies the Azure cloud environment endpoints to use for
connecting and authenticating with Azure. By default it points to the public cloud AAD endpoint.
The following endpoints are available, also see here: <a href="https://github.com/Azure/go-autorest/blob/main/autorest/azure/environments.go#L152">https://github.com/Azure/go-autorest/blob/main/autorest/azure/environments.go#L152</a>
PublicCloud, USGovernmentCloud, ChinaCloud, GermanCloud</p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;ChinaCloud&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;GermanCloud&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;PublicCloud&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;USGovernmentCloud&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AzureKVAuth">AzureKVAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AzureKVProvider">AzureKVProvider</a>)
</p>
<p>
<p>Configuration used to authenticate with Azure.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>clientId</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The Azure clientId of the service principle used for authentication.</p>
</td>
</tr>
<tr>
<td>
<code>clientSecret</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The Azure ClientSecret of the service principle used for authentication.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.AzureKVProvider">AzureKVProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>Configures an store to sync secrets using Azure KV.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>authType</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AzureAuthType">
AzureAuthType
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Auth type defines how to authenticate to the keyvault service.
Valid values are:
- &ldquo;ServicePrincipal&rdquo; (default): Using a service principal (tenantId, clientId, clientSecret)
- &ldquo;ManagedIdentity&rdquo;: Using Managed Identity assigned to the pod (see aad-pod-identity)</p>
</td>
</tr>
<tr>
<td>
<code>vaultUrl</code></br>
<em>
string
</em>
</td>
<td>
<p>Vault Url from which the secrets to be fetched from.</p>
</td>
</tr>
<tr>
<td>
<code>tenantId</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>TenantID configures the Azure Tenant to send requests to. Required for ServicePrincipal auth type.</p>
</td>
</tr>
<tr>
<td>
<code>environmentType</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AzureEnvironmentType">
AzureEnvironmentType
</a>
</em>
</td>
<td>
<p>EnvironmentType specifies the Azure cloud environment endpoints to use for
connecting and authenticating with Azure. By default it points to the public cloud AAD endpoint.
The following endpoints are available, also see here: <a href="https://github.com/Azure/go-autorest/blob/main/autorest/azure/environments.go#L152">https://github.com/Azure/go-autorest/blob/main/autorest/azure/environments.go#L152</a>
PublicCloud, USGovernmentCloud, ChinaCloud, GermanCloud</p>
</td>
</tr>
<tr>
<td>
<code>authSecretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AzureKVAuth">
AzureKVAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Auth configures how the operator authenticates with Azure. Required for ServicePrincipal auth type.</p>
</td>
</tr>
<tr>
<td>
<code>serviceAccountRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#ServiceAccountSelector">
External Secrets meta/v1.ServiceAccountSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ServiceAccountRef specified the service account
that should be used when authenticating with WorkloadIdentity.</p>
</td>
</tr>
<tr>
<td>
<code>identityId</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>If multiple Managed Identity is assigned to the pod, you can select the one to be used</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.CAProvider">CAProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.AkeylessProvider">AkeylessProvider</a>, 
<a href="#external-secrets.io/v1beta1.KubernetesServer">KubernetesServer</a>, 
<a href="#external-secrets.io/v1beta1.VaultProvider">VaultProvider</a>)
</p>
<p>
<p>Used to provide custom certificate authority (CA) certificates
for a secret store. The CAProvider points to a Secret or ConfigMap resource
that contains a PEM-encoded certificate.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code></br>
<em>
<a href="#external-secrets.io/v1beta1.CAProviderType">
CAProviderType
</a>
</em>
</td>
<td>
<p>The type of provider to use such as &ldquo;Secret&rdquo;, or &ldquo;ConfigMap&rdquo;.</p>
</td>
</tr>
<tr>
<td>
<code>name</code></br>
<em>
string
</em>
</td>
<td>
<p>The name of the object located at the provider type.</p>
</td>
</tr>
<tr>
<td>
<code>key</code></br>
<em>
string
</em>
</td>
<td>
<p>The key where the CA certificate can be found in the Secret or ConfigMap.</p>
</td>
</tr>
<tr>
<td>
<code>namespace</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>The namespace the Provider type is in.
Can only be defined when used in a ClusterSecretStore.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.CAProviderType">CAProviderType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.CAProvider">CAProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;ConfigMap&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Secret&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.CertAuth">CertAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.KubernetesAuth">KubernetesAuth</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>clientCert</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>clientKey</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ClusterExternalSecret">ClusterExternalSecret
</h3>
<p>
<p>ClusterExternalSecret is the Schema for the clusterexternalsecrets API.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretSpec">
ClusterExternalSecretSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>externalSecretSpec</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretSpec">
ExternalSecretSpec
</a>
</em>
</td>
<td>
<p>The spec for the ExternalSecrets to be created</p>
</td>
</tr>
<tr>
<td>
<code>externalSecretName</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>The name of the external secrets to be created defaults to the name of the ClusterExternalSecret</p>
</td>
</tr>
<tr>
<td>
<code>externalSecretMetadata</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretMetadata">
ExternalSecretMetadata
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The metadata of the external secrets to be created</p>
</td>
</tr>
<tr>
<td>
<code>namespaceSelector</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#labelselector-v1-meta">
Kubernetes meta/v1.LabelSelector
</a>
</em>
</td>
<td>
<p>The labels to select by to find the Namespaces to create the ExternalSecrets in.</p>
</td>
</tr>
<tr>
<td>
<code>refreshTime</code></br>
<em>
<a href="https://pkg.go.dev/k8s.io/apimachinery/pkg/apis/meta/v1#Duration">
Kubernetes meta/v1.Duration
</a>
</em>
</td>
<td>
<p>The time in which the controller should reconcile it&rsquo;s objects and recheck namespaces for labels.</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretStatus">
ClusterExternalSecretStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ClusterExternalSecretConditionType">ClusterExternalSecretConditionType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretStatusCondition">ClusterExternalSecretStatusCondition</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;NotReady&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;PartiallyReady&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Ready&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ClusterExternalSecretNamespaceFailure">ClusterExternalSecretNamespaceFailure
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretStatus">ClusterExternalSecretStatus</a>)
</p>
<p>
<p>ClusterExternalSecretNamespaceFailure represents a failed namespace deployment and it&rsquo;s reason.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>namespace</code></br>
<em>
string
</em>
</td>
<td>
<p>Namespace is the namespace that failed when trying to apply an ExternalSecret</p>
</td>
</tr>
<tr>
<td>
<code>reason</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Reason is why the ExternalSecret failed to apply to the namespace</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ClusterExternalSecretSpec">ClusterExternalSecretSpec
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecret">ClusterExternalSecret</a>)
</p>
<p>
<p>ClusterExternalSecretSpec defines the desired state of ClusterExternalSecret.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>externalSecretSpec</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretSpec">
ExternalSecretSpec
</a>
</em>
</td>
<td>
<p>The spec for the ExternalSecrets to be created</p>
</td>
</tr>
<tr>
<td>
<code>externalSecretName</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>The name of the external secrets to be created defaults to the name of the ClusterExternalSecret</p>
</td>
</tr>
<tr>
<td>
<code>externalSecretMetadata</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretMetadata">
ExternalSecretMetadata
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The metadata of the external secrets to be created</p>
</td>
</tr>
<tr>
<td>
<code>namespaceSelector</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#labelselector-v1-meta">
Kubernetes meta/v1.LabelSelector
</a>
</em>
</td>
<td>
<p>The labels to select by to find the Namespaces to create the ExternalSecrets in.</p>
</td>
</tr>
<tr>
<td>
<code>refreshTime</code></br>
<em>
<a href="https://pkg.go.dev/k8s.io/apimachinery/pkg/apis/meta/v1#Duration">
Kubernetes meta/v1.Duration
</a>
</em>
</td>
<td>
<p>The time in which the controller should reconcile it&rsquo;s objects and recheck namespaces for labels.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ClusterExternalSecretStatus">ClusterExternalSecretStatus
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecret">ClusterExternalSecret</a>)
</p>
<p>
<p>ClusterExternalSecretStatus defines the observed state of ClusterExternalSecret.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>failedNamespaces</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretNamespaceFailure">
[]ClusterExternalSecretNamespaceFailure
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Failed namespaces are the namespaces that failed to apply an ExternalSecret</p>
</td>
</tr>
<tr>
<td>
<code>provisionedNamespaces</code></br>
<em>
[]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>ProvisionedNamespaces are the namespaces where the ClusterExternalSecret has secrets</p>
</td>
</tr>
<tr>
<td>
<code>conditions</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretStatusCondition">
[]ClusterExternalSecretStatusCondition
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ClusterExternalSecretStatusCondition">ClusterExternalSecretStatusCondition
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretStatus">ClusterExternalSecretStatus</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretConditionType">
ClusterExternalSecretConditionType
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>status</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#conditionstatus-v1-core">
Kubernetes core/v1.ConditionStatus
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>message</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ClusterSecretStore">ClusterSecretStore
</h3>
<p>
<p>ClusterSecretStore represents a secure external location for storing secrets, which can be referenced as part of <code>storeRef</code> fields.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreSpec">
SecretStoreSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>controller</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to select the correct ESO controller (think: ingress.ingressClassName)
The ESO controller is instantiated with a specific controller name and filters ES based on this property</p>
</td>
</tr>
<tr>
<td>
<code>provider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">
SecretStoreProvider
</a>
</em>
</td>
<td>
<p>Used to configure the provider. Only one provider may be set</p>
</td>
</tr>
<tr>
<td>
<code>retrySettings</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreRetrySettings">
SecretStoreRetrySettings
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to configure http retries if failed</p>
</td>
</tr>
<tr>
<td>
<code>refreshInterval</code></br>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to configure store refresh interval in seconds. Empty or 0 will default to the controller config.</p>
</td>
</tr>
<tr>
<td>
<code>conditions</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ClusterSecretStoreCondition">
[]ClusterSecretStoreCondition
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to constraint a ClusterSecretStore to specific namespaces. Relevant only to ClusterSecretStore</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreStatus">
SecretStoreStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ClusterSecretStoreCondition">ClusterSecretStoreCondition
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreSpec">SecretStoreSpec</a>)
</p>
<p>
<p>ClusterSecretStoreCondition describes a condition by which to choose namespaces to process ExternalSecrets in
for a ClusterSecretStore instance.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>namespaceSelector</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#labelselector-v1-meta">
Kubernetes meta/v1.LabelSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Choose namespace using a labelSelector</p>
</td>
</tr>
<tr>
<td>
<code>namespaces</code></br>
<em>
[]string
</em>
</td>
<td>
<p>Choose namespaces by name</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.DopplerAuth">DopplerAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.DopplerProvider">DopplerProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.DopplerAuthSecretRef">
DopplerAuthSecretRef
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.DopplerAuthSecretRef">DopplerAuthSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.DopplerAuth">DopplerAuth</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>dopplerToken</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The DopplerToken is used for authentication.
See <a href="https://docs.doppler.com/reference/api#authentication">https://docs.doppler.com/reference/api#authentication</a> for auth token types.
The Key attribute defaults to dopplerToken if not specified.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.DopplerProvider">DopplerProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>DopplerProvider configures a store to sync secrets using the Doppler provider.
Project and Config are required if not using a Service Token.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.DopplerAuth">
DopplerAuth
</a>
</em>
</td>
<td>
<p>Auth configures how the Operator authenticates with the Doppler API</p>
</td>
</tr>
<tr>
<td>
<code>project</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Doppler project (required if not using a Service Token)</p>
</td>
</tr>
<tr>
<td>
<code>config</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Doppler config (required if not using a Service Token)</p>
</td>
</tr>
<tr>
<td>
<code>nameTransformer</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Environment variable compatible name transforms that change secret names to a different format</p>
</td>
</tr>
<tr>
<td>
<code>format</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Format enables the downloading of secrets as a file (string)</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecret">ExternalSecret
</h3>
<p>
<p>ExternalSecret is the Schema for the external-secrets API.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretSpec">
ExternalSecretSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>secretStoreRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreRef">
SecretStoreRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>target</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTarget">
ExternalSecretTarget
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>refreshInterval</code></br>
<em>
<a href="https://pkg.go.dev/k8s.io/apimachinery/pkg/apis/meta/v1#Duration">
Kubernetes meta/v1.Duration
</a>
</em>
</td>
<td>
<p>RefreshInterval is the amount of time before the values are read again from the SecretStore provider
Valid time units are &ldquo;ns&rdquo;, &ldquo;us&rdquo; (or &ldquo;µs&rdquo;), &ldquo;ms&rdquo;, &ldquo;s&rdquo;, &ldquo;m&rdquo;, &ldquo;h&rdquo;
May be set to zero to fetch and create it once. Defaults to 1h.</p>
</td>
</tr>
<tr>
<td>
<code>data</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretData">
[]ExternalSecretData
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Data defines the connection between the Kubernetes Secret keys and the Provider data</p>
</td>
</tr>
<tr>
<td>
<code>dataFrom</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataFromRemoteRef">
[]ExternalSecretDataFromRemoteRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>DataFrom is used to fetch all properties from a specific Provider data
If multiple entries are specified, the Secret keys are merged in the specified order</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretStatus">
ExternalSecretStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretConditionType">ExternalSecretConditionType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretStatusCondition">ExternalSecretStatusCondition</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Deleted&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Ready&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretConversionStrategy">ExternalSecretConversionStrategy
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataRemoteRef">ExternalSecretDataRemoteRef</a>, 
<a href="#external-secrets.io/v1beta1.ExternalSecretFind">ExternalSecretFind</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Default&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Unicode&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretCreationPolicy">ExternalSecretCreationPolicy
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTarget">ExternalSecretTarget</a>)
</p>
<p>
<p>ExternalSecretCreationPolicy defines rules on how to create the resulting Secret.</p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Merge&#34;</p></td>
<td><p>Merge does not create the Secret, but merges the data fields to the Secret.</p>
</td>
</tr><tr><td><p>&#34;None&#34;</p></td>
<td><p>None does not create a Secret (future use with injector).</p>
</td>
</tr><tr><td><p>&#34;Orphan&#34;</p></td>
<td><p>Orphan creates the Secret and does not set the ownerReference.
I.e. it will be orphaned after the deletion of the ExternalSecret.</p>
</td>
</tr><tr><td><p>&#34;Owner&#34;</p></td>
<td><p>Owner creates the Secret and sets .metadata.ownerReferences to the ExternalSecret resource.</p>
</td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretData">ExternalSecretData
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretSpec">ExternalSecretSpec</a>)
</p>
<p>
<p>ExternalSecretData defines the connection between the Kubernetes Secret key (spec.data.<key>) and the Provider data.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretKey</code></br>
<em>
string
</em>
</td>
<td>
<p>SecretKey defines the key in which the controller stores
the value. This is the key in the Kind=Secret</p>
</td>
</tr>
<tr>
<td>
<code>remoteRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataRemoteRef">
ExternalSecretDataRemoteRef
</a>
</em>
</td>
<td>
<p>RemoteRef points to the remote secret and defines
which secret (version/property/..) to fetch.</p>
</td>
</tr>
<tr>
<td>
<code>sourceRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SourceRef">
SourceRef
</a>
</em>
</td>
<td>
<p>SourceRef allows you to override the source
from which the value will pulled from.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretDataFromRemoteRef">ExternalSecretDataFromRemoteRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretSpec">ExternalSecretSpec</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>extract</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataRemoteRef">
ExternalSecretDataRemoteRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to extract multiple key/value pairs from one secret
Note: Extract does not support sourceRef.Generator or sourceRef.GeneratorRef.</p>
</td>
</tr>
<tr>
<td>
<code>find</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretFind">
ExternalSecretFind
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to find secrets based on tags or regular expressions
Note: Find does not support sourceRef.Generator or sourceRef.GeneratorRef.</p>
</td>
</tr>
<tr>
<td>
<code>rewrite</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretRewrite">
[]ExternalSecretRewrite
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to rewrite secret Keys after getting them from the secret Provider
Multiple Rewrite operations can be provided. They are applied in a layered order (first to last)</p>
</td>
</tr>
<tr>
<td>
<code>sourceRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SourceRef">
SourceRef
</a>
</em>
</td>
<td>
<p>SourceRef points to a store or generator
which contains secret values ready to use.
Use this in combination with Extract or Find pull values out of
a specific SecretStore.
When sourceRef points to a generator Extract or Find is not supported.
The generator returns a static map of values</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretDataRemoteRef">ExternalSecretDataRemoteRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretData">ExternalSecretData</a>, 
<a href="#external-secrets.io/v1beta1.ExternalSecretDataFromRemoteRef">ExternalSecretDataFromRemoteRef</a>)
</p>
<p>
<p>ExternalSecretDataRemoteRef defines Provider data location.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>key</code></br>
<em>
string
</em>
</td>
<td>
<p>Key is the key used in the Provider, mandatory</p>
</td>
</tr>
<tr>
<td>
<code>metadataPolicy</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretMetadataPolicy">
ExternalSecretMetadataPolicy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Policy for fetching tags/labels from provider secrets, possible options are Fetch, None. Defaults to None</p>
</td>
</tr>
<tr>
<td>
<code>property</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to select a specific property of the Provider value (if a map), if supported</p>
</td>
</tr>
<tr>
<td>
<code>version</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to select a specific version of the Provider value, if supported</p>
</td>
</tr>
<tr>
<td>
<code>conversionStrategy</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretConversionStrategy">
ExternalSecretConversionStrategy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to define a conversion Strategy</p>
</td>
</tr>
<tr>
<td>
<code>decodingStrategy</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDecodingStrategy">
ExternalSecretDecodingStrategy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to define a decoding Strategy</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretDecodingStrategy">ExternalSecretDecodingStrategy
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataRemoteRef">ExternalSecretDataRemoteRef</a>, 
<a href="#external-secrets.io/v1beta1.ExternalSecretFind">ExternalSecretFind</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Auto&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Base64&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Base64URL&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;None&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretDeletionPolicy">ExternalSecretDeletionPolicy
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTarget">ExternalSecretTarget</a>)
</p>
<p>
<p>ExternalSecretDeletionPolicy defines rules on how to delete the resulting Secret.</p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Delete&#34;</p></td>
<td><p>Delete deletes the secret if all provider secrets are deleted.
If a secret gets deleted on the provider side and is not accessible
anymore this is not considered an error and the ExternalSecret
does not go into SecretSyncedError status.</p>
</td>
</tr><tr><td><p>&#34;Merge&#34;</p></td>
<td><p>Merge removes keys in the secret, but not the secret itself.
If a secret gets deleted on the provider side and is not accessible
anymore this is not considered an error and the ExternalSecret
does not go into SecretSyncedError status.</p>
</td>
</tr><tr><td><p>&#34;Retain&#34;</p></td>
<td><p>Retain will retain the secret if all provider secrets have been deleted.
If a provider secret does not exist the ExternalSecret gets into the
SecretSyncedError status.</p>
</td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretFind">ExternalSecretFind
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataFromRemoteRef">ExternalSecretDataFromRemoteRef</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>path</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>A root path to start the find operations.</p>
</td>
</tr>
<tr>
<td>
<code>name</code></br>
<em>
<a href="#external-secrets.io/v1beta1.FindName">
FindName
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Finds secrets based on the name.</p>
</td>
</tr>
<tr>
<td>
<code>tags</code></br>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Find secrets based on tags.</p>
</td>
</tr>
<tr>
<td>
<code>conversionStrategy</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretConversionStrategy">
ExternalSecretConversionStrategy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to define a conversion Strategy</p>
</td>
</tr>
<tr>
<td>
<code>decodingStrategy</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDecodingStrategy">
ExternalSecretDecodingStrategy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to define a decoding Strategy</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretMetadata">ExternalSecretMetadata
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretSpec">ClusterExternalSecretSpec</a>)
</p>
<p>
<p>ExternalSecretMetadata defines metadata fields for the ExternalSecret generated by the ClusterExternalSecret.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>annotations</code></br>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>labels</code></br>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretMetadataPolicy">ExternalSecretMetadataPolicy
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataRemoteRef">ExternalSecretDataRemoteRef</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Fetch&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;None&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretRewrite">ExternalSecretRewrite
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataFromRemoteRef">ExternalSecretDataFromRemoteRef</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>regexp</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretRewriteRegexp">
ExternalSecretRewriteRegexp
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to rewrite with regular expressions.
The resulting key will be the output of a regexp.ReplaceAll operation.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretRewriteRegexp">ExternalSecretRewriteRegexp
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretRewrite">ExternalSecretRewrite</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>source</code></br>
<em>
string
</em>
</td>
<td>
<p>Used to define the regular expression of a re.Compiler.</p>
</td>
</tr>
<tr>
<td>
<code>target</code></br>
<em>
string
</em>
</td>
<td>
<p>Used to define the target pattern of a ReplaceAll operation.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretSpec">ExternalSecretSpec
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterExternalSecretSpec">ClusterExternalSecretSpec</a>, 
<a href="#external-secrets.io/v1beta1.ExternalSecret">ExternalSecret</a>)
</p>
<p>
<p>ExternalSecretSpec defines the desired state of ExternalSecret.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretStoreRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreRef">
SecretStoreRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>target</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTarget">
ExternalSecretTarget
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>refreshInterval</code></br>
<em>
<a href="https://pkg.go.dev/k8s.io/apimachinery/pkg/apis/meta/v1#Duration">
Kubernetes meta/v1.Duration
</a>
</em>
</td>
<td>
<p>RefreshInterval is the amount of time before the values are read again from the SecretStore provider
Valid time units are &ldquo;ns&rdquo;, &ldquo;us&rdquo; (or &ldquo;µs&rdquo;), &ldquo;ms&rdquo;, &ldquo;s&rdquo;, &ldquo;m&rdquo;, &ldquo;h&rdquo;
May be set to zero to fetch and create it once. Defaults to 1h.</p>
</td>
</tr>
<tr>
<td>
<code>data</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretData">
[]ExternalSecretData
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Data defines the connection between the Kubernetes Secret keys and the Provider data</p>
</td>
</tr>
<tr>
<td>
<code>dataFrom</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDataFromRemoteRef">
[]ExternalSecretDataFromRemoteRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>DataFrom is used to fetch all properties from a specific Provider data
If multiple entries are specified, the Secret keys are merged in the specified order</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretStatus">ExternalSecretStatus
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecret">ExternalSecret</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>refreshTime</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#time-v1-meta">
Kubernetes meta/v1.Time
</a>
</em>
</td>
<td>
<p>refreshTime is the time and date the external secret was fetched and
the target secret updated</p>
</td>
</tr>
<tr>
<td>
<code>syncedResourceVersion</code></br>
<em>
string
</em>
</td>
<td>
<p>SyncedResourceVersion keeps track of the last synced version</p>
</td>
</tr>
<tr>
<td>
<code>conditions</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretStatusCondition">
[]ExternalSecretStatusCondition
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>binding</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#localobjectreference-v1-core">
Kubernetes core/v1.LocalObjectReference
</a>
</em>
</td>
<td>
<p>Binding represents a servicebinding.io Provisioned Service reference to the secret</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretStatusCondition">ExternalSecretStatusCondition
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretStatus">ExternalSecretStatus</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretConditionType">
ExternalSecretConditionType
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>status</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#conditionstatus-v1-core">
Kubernetes core/v1.ConditionStatus
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>reason</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>message</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>lastTransitionTime</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#time-v1-meta">
Kubernetes meta/v1.Time
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretTarget">ExternalSecretTarget
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretSpec">ExternalSecretSpec</a>)
</p>
<p>
<p>ExternalSecretTarget defines the Kubernetes Secret to be created
There can be only one target per ExternalSecret.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>name</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Name defines the name of the Secret resource to be managed
This field is immutable
Defaults to the .metadata.name of the ExternalSecret resource</p>
</td>
</tr>
<tr>
<td>
<code>creationPolicy</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretCreationPolicy">
ExternalSecretCreationPolicy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>CreationPolicy defines rules on how to create the resulting Secret
Defaults to &lsquo;Owner&rsquo;</p>
</td>
</tr>
<tr>
<td>
<code>deletionPolicy</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretDeletionPolicy">
ExternalSecretDeletionPolicy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>DeletionPolicy defines rules on how to delete the resulting Secret
Defaults to &lsquo;Retain&rsquo;</p>
</td>
</tr>
<tr>
<td>
<code>template</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTemplate">
ExternalSecretTemplate
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Template defines a blueprint for the created Secret resource.</p>
</td>
</tr>
<tr>
<td>
<code>immutable</code></br>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Immutable defines if the final secret will be immutable</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretTemplate">ExternalSecretTemplate
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTarget">ExternalSecretTarget</a>)
</p>
<p>
<p>ExternalSecretTemplate defines a blueprint for the created Secret resource.
we can not use native corev1.Secret, it will have empty ObjectMeta values: <a href="https://github.com/kubernetes-sigs/controller-tools/issues/448">https://github.com/kubernetes-sigs/controller-tools/issues/448</a></p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#secrettype-v1-core">
Kubernetes core/v1.SecretType
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>engineVersion</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TemplateEngineVersion">
TemplateEngineVersion
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>metadata</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTemplateMetadata">
ExternalSecretTemplateMetadata
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>mergePolicy</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TemplateMergePolicy">
TemplateMergePolicy
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>data</code></br>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>templateFrom</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TemplateFrom">
[]TemplateFrom
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretTemplateMetadata">ExternalSecretTemplateMetadata
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTemplate">ExternalSecretTemplate</a>)
</p>
<p>
<p>ExternalSecretTemplateMetadata defines metadata fields for the Secret blueprint.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>annotations</code></br>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>labels</code></br>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ExternalSecretValidator">ExternalSecretValidator
</h3>
<p>
</p>
<h3 id="external-secrets.io/v1beta1.FakeProvider">FakeProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>FakeProvider configures a fake provider that returns static values.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>data</code></br>
<em>
<a href="#external-secrets.io/v1beta1.FakeProviderData">
[]FakeProviderData
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.FakeProviderData">FakeProviderData
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.FakeProvider">FakeProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>key</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>value</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>valueMap</code></br>
<em>
map[string]string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>version</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.FindName">FindName
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretFind">ExternalSecretFind</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>regexp</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Finds secrets base</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.GCPSMAuth">GCPSMAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.GCPSMProvider">GCPSMProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.GCPSMAuthSecretRef">
GCPSMAuthSecretRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>workloadIdentity</code></br>
<em>
<a href="#external-secrets.io/v1beta1.GCPWorkloadIdentity">
GCPWorkloadIdentity
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.GCPSMAuthSecretRef">GCPSMAuthSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.GCPSMAuth">GCPSMAuth</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretAccessKeySecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The SecretAccessKey is used for authentication</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.GCPSMProvider">GCPSMProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>GCPSMProvider Configures a store to sync secrets using the GCP Secret Manager provider.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.GCPSMAuth">
GCPSMAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Auth defines the information necessary to authenticate against GCP</p>
</td>
</tr>
<tr>
<td>
<code>projectID</code></br>
<em>
string
</em>
</td>
<td>
<p>ProjectID project where secret is located</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.GCPWorkloadIdentity">GCPWorkloadIdentity
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.GCPSMAuth">GCPSMAuth</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>serviceAccountRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#ServiceAccountSelector">
External Secrets meta/v1.ServiceAccountSelector
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>clusterLocation</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>clusterName</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>clusterProjectID</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.GeneratorRef">GeneratorRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SourceRef">SourceRef</a>)
</p>
<p>
<p>GeneratorRef points to a generator custom resource.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>apiVersion</code></br>
<em>
string
</em>
</td>
<td>
<p>Specify the apiVersion of the generator resource</p>
</td>
</tr>
<tr>
<td>
<code>kind</code></br>
<em>
string
</em>
</td>
<td>
<p>Specify the Kind of the resource, e.g. Password, ACRAccessToken etc.</p>
</td>
</tr>
<tr>
<td>
<code>name</code></br>
<em>
string
</em>
</td>
<td>
<p>Specify the name of the generator resource</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.GenericStore">GenericStore
</h3>
<p>
<p>GenericStore is a common interface for interacting with ClusterSecretStore
or a namespaced SecretStore.</p>
</p>
<h3 id="external-secrets.io/v1beta1.GenericStoreValidator">GenericStoreValidator
</h3>
<p>
</p>
<h3 id="external-secrets.io/v1beta1.GitlabAuth">GitlabAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.GitlabProvider">GitlabProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>SecretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.GitlabSecretRef">
GitlabSecretRef
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.GitlabProvider">GitlabProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>Configures a store to sync secrets with a GitLab instance.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>url</code></br>
<em>
string
</em>
</td>
<td>
<p>URL configures the GitLab instance URL. Defaults to <a href="https://gitlab.com/">https://gitlab.com/</a>.</p>
</td>
</tr>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.GitlabAuth">
GitlabAuth
</a>
</em>
</td>
<td>
<p>Auth configures how secret-manager authenticates with a GitLab instance.</p>
</td>
</tr>
<tr>
<td>
<code>projectID</code></br>
<em>
string
</em>
</td>
<td>
<p>ProjectID specifies a project where secrets are located.</p>
</td>
</tr>
<tr>
<td>
<code>inheritFromGroups</code></br>
<em>
bool
</em>
</td>
<td>
<p>InheritFromGroups specifies whether parent groups should be discovered and checked for secrets.</p>
</td>
</tr>
<tr>
<td>
<code>groupIDs</code></br>
<em>
[]string
</em>
</td>
<td>
<p>GroupIDs specify, which gitlab groups to pull secrets from. Group secrets are read from left to right followed by the project variables.</p>
</td>
</tr>
<tr>
<td>
<code>environment</code></br>
<em>
string
</em>
</td>
<td>
<p>Environment environment_scope of gitlab CI/CD variables (Please see <a href="https://docs.gitlab.com/ee/ci/environments/#create-a-static-environment">https://docs.gitlab.com/ee/ci/environments/#create-a-static-environment</a> on how to create environments)</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.GitlabSecretRef">GitlabSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.GitlabAuth">GitlabAuth</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>accessToken</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>AccessToken is used for authentication.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.IBMAuth">IBMAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.IBMProvider">IBMProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.IBMAuthSecretRef">
IBMAuthSecretRef
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>containerAuth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.IBMAuthContainerAuth">
IBMAuthContainerAuth
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.IBMAuthContainerAuth">IBMAuthContainerAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.IBMAuth">IBMAuth</a>)
</p>
<p>
<p>IBM Container-based auth with IAM Trusted Profile.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>profile</code></br>
<em>
string
</em>
</td>
<td>
<p>the IBM Trusted Profile</p>
</td>
</tr>
<tr>
<td>
<code>tokenLocation</code></br>
<em>
string
</em>
</td>
<td>
<p>Location the token is mounted on the pod</p>
</td>
</tr>
<tr>
<td>
<code>iamEndpoint</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.IBMAuthSecretRef">IBMAuthSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.IBMAuth">IBMAuth</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretApiKeySecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The SecretAccessKey is used for authentication</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.IBMProvider">IBMProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>Configures an store to sync secrets using a IBM Cloud Secrets Manager
backend.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.IBMAuth">
IBMAuth
</a>
</em>
</td>
<td>
<p>Auth configures how secret-manager authenticates with the IBM secrets manager.</p>
</td>
</tr>
<tr>
<td>
<code>serviceUrl</code></br>
<em>
string
</em>
</td>
<td>
<p>ServiceURL is the Endpoint URL that is specific to the Secrets Manager service instance</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.KeeperSecurityProvider">KeeperSecurityProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>KeeperSecurityProvider Configures a store to sync secrets using Keeper Security.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>authRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>folderID</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.KubernetesAuth">KubernetesAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.KubernetesProvider">KubernetesProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>cert</code></br>
<em>
<a href="#external-secrets.io/v1beta1.CertAuth">
CertAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>has both clientCert and clientKey as secretKeySelector</p>
</td>
</tr>
<tr>
<td>
<code>token</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TokenAuth">
TokenAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>use static token to authenticate with</p>
</td>
</tr>
<tr>
<td>
<code>serviceAccount</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#ServiceAccountSelector">
External Secrets meta/v1.ServiceAccountSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>points to a service account that should be used for authentication</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.KubernetesProvider">KubernetesProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>Configures a store to sync secrets with a Kubernetes instance.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>server</code></br>
<em>
<a href="#external-secrets.io/v1beta1.KubernetesServer">
KubernetesServer
</a>
</em>
</td>
<td>
<p>configures the Kubernetes server Address.</p>
</td>
</tr>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.KubernetesAuth">
KubernetesAuth
</a>
</em>
</td>
<td>
<p>Auth configures how secret-manager authenticates with a Kubernetes instance.</p>
</td>
</tr>
<tr>
<td>
<code>remoteNamespace</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Remote namespace to fetch the secrets from</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.KubernetesServer">KubernetesServer
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.KubernetesProvider">KubernetesProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>url</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>configures the Kubernetes server Address.</p>
</td>
</tr>
<tr>
<td>
<code>caBundle</code></br>
<em>
[]byte
</em>
</td>
<td>
<em>(Optional)</em>
<p>CABundle is a base64-encoded CA certificate</p>
</td>
</tr>
<tr>
<td>
<code>caProvider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.CAProvider">
CAProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>see: <a href="https://external-secrets.io/v0.4.1/spec/#external-secrets.io/v1alpha1.CAProvider">https://external-secrets.io/v0.4.1/spec/#external-secrets.io/v1alpha1.CAProvider</a></p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.NoSecretError">NoSecretError
</h3>
<p>
<p>NoSecretError shall be returned when a GetSecret can not find the
desired secret. This is used for deletionPolicy.</p>
</p>
<h3 id="external-secrets.io/v1beta1.OnePasswordAuth">OnePasswordAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.OnePasswordProvider">OnePasswordProvider</a>)
</p>
<p>
<p>OnePasswordAuth contains a secretRef for credentials.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.OnePasswordAuthSecretRef">
OnePasswordAuthSecretRef
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.OnePasswordAuthSecretRef">OnePasswordAuthSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.OnePasswordAuth">OnePasswordAuth</a>)
</p>
<p>
<p>OnePasswordAuthSecretRef holds secret references for 1Password credentials.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>connectTokenSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The ConnectToken is used for authentication to a 1Password Connect Server.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.OnePasswordProvider">OnePasswordProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>OnePasswordProvider configures a store to sync secrets using the 1Password Secret Manager provider.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.OnePasswordAuth">
OnePasswordAuth
</a>
</em>
</td>
<td>
<p>Auth defines the information necessary to authenticate against OnePassword Connect Server</p>
</td>
</tr>
<tr>
<td>
<code>connectHost</code></br>
<em>
string
</em>
</td>
<td>
<p>ConnectHost defines the OnePassword Connect Server to connect to</p>
</td>
</tr>
<tr>
<td>
<code>vaults</code></br>
<em>
map[string]int
</em>
</td>
<td>
<p>Vaults defines which OnePassword vaults to search in which order</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.OracleAuth">OracleAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.OracleProvider">OracleProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>tenancy</code></br>
<em>
string
</em>
</td>
<td>
<p>Tenancy is the tenancy OCID where user is located.</p>
</td>
</tr>
<tr>
<td>
<code>user</code></br>
<em>
string
</em>
</td>
<td>
<p>User is an access OCID specific to the account.</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.OracleSecretRef">
OracleSecretRef
</a>
</em>
</td>
<td>
<p>SecretRef to pass through sensitive information.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.OracleProvider">OracleProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>Configures an store to sync secrets using a Oracle Vault
backend.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>region</code></br>
<em>
string
</em>
</td>
<td>
<p>Region is the region where vault is located.</p>
</td>
</tr>
<tr>
<td>
<code>vault</code></br>
<em>
string
</em>
</td>
<td>
<p>Vault is the vault&rsquo;s OCID of the specific vault where secret is located.</p>
</td>
</tr>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.OracleAuth">
OracleAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Auth configures how secret-manager authenticates with the Oracle Vault.
If empty, use the instance principal, otherwise the user credentials specified in Auth.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.OracleSecretRef">OracleSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.OracleAuth">OracleAuth</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>privatekey</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>PrivateKey is the user&rsquo;s API Signing Key in PEM format, used for authentication.</p>
</td>
</tr>
<tr>
<td>
<code>fingerprint</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>Fingerprint is the fingerprint of the API private key.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.Provider">Provider
</h3>
<p>
<p>Provider is a common interface for interacting with secret backends.</p>
</p>
<h3 id="external-secrets.io/v1beta1.PushRemoteRef">PushRemoteRef
</h3>
<p>
<p>This interface is to allow using v1alpha1 content in Provider registered in v1beta1.</p>
</p>
<h3 id="external-secrets.io/v1beta1.ScalewayProvider">ScalewayProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>apiUrl</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>APIURL is the url of the api to use. Defaults to <a href="https://api.scaleway.com">https://api.scaleway.com</a></p>
</td>
</tr>
<tr>
<td>
<code>region</code></br>
<em>
string
</em>
</td>
<td>
<p>Region where your secrets are located: <a href="https://developers.scaleway.com/en/quickstart/#region-and-zone">https://developers.scaleway.com/en/quickstart/#region-and-zone</a></p>
</td>
</tr>
<tr>
<td>
<code>projectId</code></br>
<em>
string
</em>
</td>
<td>
<p>ProjectID is the id of your project, which you can find in the console: <a href="https://console.scaleway.com/project/settings">https://console.scaleway.com/project/settings</a></p>
</td>
</tr>
<tr>
<td>
<code>accessKey</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ScalewayProviderSecretRef">
ScalewayProviderSecretRef
</a>
</em>
</td>
<td>
<p>AccessKey is the non-secret part of the api key.</p>
</td>
</tr>
<tr>
<td>
<code>secretKey</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ScalewayProviderSecretRef">
ScalewayProviderSecretRef
</a>
</em>
</td>
<td>
<p>SecretKey is the non-secret part of the api key.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ScalewayProviderSecretRef">ScalewayProviderSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ScalewayProvider">ScalewayProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>value</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Value can be specified directly to set a value without using a secret.</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>SecretRef references a key in a secret that will be used as value.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStore">SecretStore
</h3>
<p>
<p>SecretStore represents a secure external location for storing secrets, which can be referenced as part of <code>storeRef</code> fields.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreSpec">
SecretStoreSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>controller</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to select the correct ESO controller (think: ingress.ingressClassName)
The ESO controller is instantiated with a specific controller name and filters ES based on this property</p>
</td>
</tr>
<tr>
<td>
<code>provider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">
SecretStoreProvider
</a>
</em>
</td>
<td>
<p>Used to configure the provider. Only one provider may be set</p>
</td>
</tr>
<tr>
<td>
<code>retrySettings</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreRetrySettings">
SecretStoreRetrySettings
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to configure http retries if failed</p>
</td>
</tr>
<tr>
<td>
<code>refreshInterval</code></br>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to configure store refresh interval in seconds. Empty or 0 will default to the controller config.</p>
</td>
</tr>
<tr>
<td>
<code>conditions</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ClusterSecretStoreCondition">
[]ClusterSecretStoreCondition
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to constraint a ClusterSecretStore to specific namespaces. Relevant only to ClusterSecretStore</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreStatus">
SecretStoreStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStoreCapabilities">SecretStoreCapabilities
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreStatus">SecretStoreStatus</a>)
</p>
<p>
<p>SecretStoreCapabilities defines the possible operations a SecretStore can do.</p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;ReadOnly&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;ReadWrite&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;WriteOnly&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStoreConditionType">SecretStoreConditionType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreStatusCondition">SecretStoreStatusCondition</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Ready&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreSpec">SecretStoreSpec</a>)
</p>
<p>
<p>SecretStoreProvider contains the provider-specific configuration.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>aws</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AWSProvider">
AWSProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>AWS configures this store to sync secrets using AWS Secret Manager provider</p>
</td>
</tr>
<tr>
<td>
<code>azurekv</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AzureKVProvider">
AzureKVProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>AzureKV configures this store to sync secrets using Azure Key Vault provider</p>
</td>
</tr>
<tr>
<td>
<code>akeyless</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AkeylessProvider">
AkeylessProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Akeyless configures this store to sync secrets using Akeyless Vault provider</p>
</td>
</tr>
<tr>
<td>
<code>vault</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultProvider">
VaultProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Vault configures this store to sync secrets using Hashi provider</p>
</td>
</tr>
<tr>
<td>
<code>gcpsm</code></br>
<em>
<a href="#external-secrets.io/v1beta1.GCPSMProvider">
GCPSMProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>GCPSM configures this store to sync secrets using Google Cloud Platform Secret Manager provider</p>
</td>
</tr>
<tr>
<td>
<code>oracle</code></br>
<em>
<a href="#external-secrets.io/v1beta1.OracleProvider">
OracleProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Oracle configures this store to sync secrets using Oracle Vault provider</p>
</td>
</tr>
<tr>
<td>
<code>ibm</code></br>
<em>
<a href="#external-secrets.io/v1beta1.IBMProvider">
IBMProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>IBM configures this store to sync secrets using IBM Cloud provider</p>
</td>
</tr>
<tr>
<td>
<code>yandexcertificatemanager</code></br>
<em>
<a href="#external-secrets.io/v1beta1.YandexCertificateManagerProvider">
YandexCertificateManagerProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>YandexCertificateManager configures this store to sync secrets using Yandex Certificate Manager provider</p>
</td>
</tr>
<tr>
<td>
<code>yandexlockbox</code></br>
<em>
<a href="#external-secrets.io/v1beta1.YandexLockboxProvider">
YandexLockboxProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>YandexLockbox configures this store to sync secrets using Yandex Lockbox provider</p>
</td>
</tr>
<tr>
<td>
<code>gitlab</code></br>
<em>
<a href="#external-secrets.io/v1beta1.GitlabProvider">
GitlabProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>GitLab configures this store to sync secrets using GitLab Variables provider</p>
</td>
</tr>
<tr>
<td>
<code>alibaba</code></br>
<em>
<a href="#external-secrets.io/v1beta1.AlibabaProvider">
AlibabaProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Alibaba configures this store to sync secrets using Alibaba Cloud provider</p>
</td>
</tr>
<tr>
<td>
<code>onepassword</code></br>
<em>
<a href="#external-secrets.io/v1beta1.OnePasswordProvider">
OnePasswordProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>OnePassword configures this store to sync secrets using the 1Password Cloud provider</p>
</td>
</tr>
<tr>
<td>
<code>webhook</code></br>
<em>
<a href="#external-secrets.io/v1beta1.WebhookProvider">
WebhookProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Webhook configures this store to sync secrets using a generic templated webhook</p>
</td>
</tr>
<tr>
<td>
<code>kubernetes</code></br>
<em>
<a href="#external-secrets.io/v1beta1.KubernetesProvider">
KubernetesProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Kubernetes configures this store to sync secrets using a Kubernetes cluster provider</p>
</td>
</tr>
<tr>
<td>
<code>fake</code></br>
<em>
<a href="#external-secrets.io/v1beta1.FakeProvider">
FakeProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Fake configures a store with static key/value pairs</p>
</td>
</tr>
<tr>
<td>
<code>senhasegura</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SenhaseguraProvider">
SenhaseguraProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Senhasegura configures this store to sync secrets using senhasegura provider</p>
</td>
</tr>
<tr>
<td>
<code>scaleway</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ScalewayProvider">
ScalewayProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Scaleway</p>
</td>
</tr>
<tr>
<td>
<code>doppler</code></br>
<em>
<a href="#external-secrets.io/v1beta1.DopplerProvider">
DopplerProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Doppler configures this store to sync secrets using the Doppler provider</p>
</td>
</tr>
<tr>
<td>
<code>keepersecurity</code></br>
<em>
<a href="#external-secrets.io/v1beta1.KeeperSecurityProvider">
KeeperSecurityProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>KeeperSecurity configures this store to sync secrets using the KeeperSecurity provider</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStoreRef">SecretStoreRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretSpec">ExternalSecretSpec</a>, 
<a href="#external-secrets.io/v1beta1.SourceRef">SourceRef</a>)
</p>
<p>
<p>SecretStoreRef defines which SecretStore to fetch the ExternalSecret data.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>name</code></br>
<em>
string
</em>
</td>
<td>
<p>Name of the SecretStore resource</p>
</td>
</tr>
<tr>
<td>
<code>kind</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Kind of the SecretStore resource (SecretStore or ClusterSecretStore)
Defaults to <code>SecretStore</code></p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStoreRetrySettings">SecretStoreRetrySettings
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreSpec">SecretStoreSpec</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>maxRetries</code></br>
<em>
int32
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>retryInterval</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStoreSpec">SecretStoreSpec
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterSecretStore">ClusterSecretStore</a>, 
<a href="#external-secrets.io/v1beta1.SecretStore">SecretStore</a>)
</p>
<p>
<p>SecretStoreSpec defines the desired state of SecretStore.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>controller</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to select the correct ESO controller (think: ingress.ingressClassName)
The ESO controller is instantiated with a specific controller name and filters ES based on this property</p>
</td>
</tr>
<tr>
<td>
<code>provider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">
SecretStoreProvider
</a>
</em>
</td>
<td>
<p>Used to configure the provider. Only one provider may be set</p>
</td>
</tr>
<tr>
<td>
<code>retrySettings</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreRetrySettings">
SecretStoreRetrySettings
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to configure http retries if failed</p>
</td>
</tr>
<tr>
<td>
<code>refreshInterval</code></br>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to configure store refresh interval in seconds. Empty or 0 will default to the controller config.</p>
</td>
</tr>
<tr>
<td>
<code>conditions</code></br>
<em>
<a href="#external-secrets.io/v1beta1.ClusterSecretStoreCondition">
[]ClusterSecretStoreCondition
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Used to constraint a ClusterSecretStore to specific namespaces. Relevant only to ClusterSecretStore</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStoreStatus">SecretStoreStatus
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ClusterSecretStore">ClusterSecretStore</a>, 
<a href="#external-secrets.io/v1beta1.SecretStore">SecretStore</a>)
</p>
<p>
<p>SecretStoreStatus defines the observed state of the SecretStore.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>conditions</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreStatusCondition">
[]SecretStoreStatusCondition
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>capabilities</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreCapabilities">
SecretStoreCapabilities
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretStoreStatusCondition">SecretStoreStatusCondition
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreStatus">SecretStoreStatus</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreConditionType">
SecretStoreConditionType
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>status</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#conditionstatus-v1-core">
Kubernetes core/v1.ConditionStatus
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>reason</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>message</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>lastTransitionTime</code></br>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#time-v1-meta">
Kubernetes meta/v1.Time
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SecretsClient">SecretsClient
</h3>
<p>
<p>SecretsClient provides access to secrets.</p>
</p>
<h3 id="external-secrets.io/v1beta1.SenhaseguraAuth">SenhaseguraAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SenhaseguraProvider">SenhaseguraProvider</a>)
</p>
<p>
<p>SenhaseguraAuth tells the controller how to do auth in senhasegura.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>clientId</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>clientSecretSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SenhaseguraModuleType">SenhaseguraModuleType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SenhaseguraProvider">SenhaseguraProvider</a>)
</p>
<p>
<p>SenhaseguraModuleType enum defines senhasegura target module to fetch secrets</p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;DSM&#34;</p></td>
<td><pre><code>	SenhaseguraModuleDSM is the senhasegura DevOps Secrets Management module
see: https://senhasegura.com/devops
</code></pre>
</td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SenhaseguraProvider">SenhaseguraProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>SenhaseguraProvider setup a store to sync secrets with senhasegura.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>url</code></br>
<em>
string
</em>
</td>
<td>
<p>URL of senhasegura</p>
</td>
</tr>
<tr>
<td>
<code>module</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SenhaseguraModuleType">
SenhaseguraModuleType
</a>
</em>
</td>
<td>
<p>Module defines which senhasegura module should be used to get secrets</p>
</td>
</tr>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SenhaseguraAuth">
SenhaseguraAuth
</a>
</em>
</td>
<td>
<p>Auth defines parameters to authenticate in senhasegura</p>
</td>
</tr>
<tr>
<td>
<code>ignoreSslCertificate</code></br>
<em>
bool
</em>
</td>
<td>
<p>IgnoreSslCertificate defines if SSL certificate must be ignored</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.SourceRef">SourceRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretData">ExternalSecretData</a>, 
<a href="#external-secrets.io/v1beta1.ExternalSecretDataFromRemoteRef">ExternalSecretDataFromRemoteRef</a>)
</p>
<p>
<p>SourceRef allows you to override the source
from which the secret will be pulled from.
You can define at maximum one property.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>storeRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.SecretStoreRef">
SecretStoreRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>generatorRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.GeneratorRef">
GeneratorRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>GeneratorRef points to a generator custom resource in</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.Tag">Tag
</h3>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>key</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>value</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.TemplateEngineVersion">TemplateEngineVersion
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTemplate">ExternalSecretTemplate</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;v1&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;v2&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.TemplateFrom">TemplateFrom
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTemplate">ExternalSecretTemplate</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>configMap</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TemplateRef">
TemplateRef
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>secret</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TemplateRef">
TemplateRef
</a>
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>target</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TemplateTarget">
TemplateTarget
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>literal</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.TemplateMergePolicy">TemplateMergePolicy
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.ExternalSecretTemplate">ExternalSecretTemplate</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Merge&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Replace&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.TemplateRef">TemplateRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.TemplateFrom">TemplateFrom</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>name</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>items</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TemplateRefItem">
[]TemplateRefItem
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.TemplateRefItem">TemplateRefItem
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.TemplateRef">TemplateRef</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>key</code></br>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>templateAs</code></br>
<em>
<a href="#external-secrets.io/v1beta1.TemplateScope">
TemplateScope
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.TemplateScope">TemplateScope
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.TemplateRefItem">TemplateRefItem</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;KeysAndValues&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Values&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.TemplateTarget">TemplateTarget
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.TemplateFrom">TemplateFrom</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Annotations&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Data&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Labels&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.TokenAuth">TokenAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.KubernetesAuth">KubernetesAuth</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>bearerToken</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.ValidationResult">ValidationResult
(<code>byte</code> alias)</p></h3>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>2</p></td>
<td><p>Error indicates that there is a misconfiguration.</p>
</td>
</tr><tr><td><p>0</p></td>
<td><p>Ready indicates that the client is configured correctly
and can be used.</p>
</td>
</tr><tr><td><p>1</p></td>
<td><p>Unknown indicates that the client can be used
but information is missing and it can not be validated.</p>
</td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultAppRole">VaultAppRole
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultAuth">VaultAuth</a>)
</p>
<p>
<p>VaultAppRole authenticates with Vault using the App Role auth mechanism,
with the role and secret stored in a Kubernetes Secret resource.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>path</code></br>
<em>
string
</em>
</td>
<td>
<p>Path where the App Role authentication backend is mounted
in Vault, e.g: &ldquo;approle&rdquo;</p>
</td>
</tr>
<tr>
<td>
<code>roleId</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>RoleID configured in the App Role authentication backend when setting
up the authentication backend in Vault.</p>
</td>
</tr>
<tr>
<td>
<code>roleRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Reference to a key in a Secret that contains the App Role ID used
to authenticate with Vault.
The <code>key</code> field must be specified and denotes which entry within the Secret
resource is used as the app role id.</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>Reference to a key in a Secret that contains the App Role secret used
to authenticate with Vault.
The <code>key</code> field must be specified and denotes which entry within the Secret
resource is used as the app role secret.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultAuth">VaultAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultProvider">VaultProvider</a>)
</p>
<p>
<p>VaultAuth is the configuration used to authenticate with a Vault server.
Only one of <code>tokenSecretRef</code>, <code>appRole</code>,  <code>kubernetes</code>, <code>ldap</code>, <code>jwt</code> or <code>cert</code>
can be specified.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>tokenSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>TokenSecretRef authenticates with Vault by presenting a token.</p>
</td>
</tr>
<tr>
<td>
<code>appRole</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultAppRole">
VaultAppRole
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>AppRole authenticates with Vault using the App Role auth mechanism,
with the role and secret stored in a Kubernetes Secret resource.</p>
</td>
</tr>
<tr>
<td>
<code>kubernetes</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultKubernetesAuth">
VaultKubernetesAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Kubernetes authenticates with Vault by passing the ServiceAccount
token stored in the named Secret resource to the Vault server.</p>
</td>
</tr>
<tr>
<td>
<code>ldap</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultLdapAuth">
VaultLdapAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Ldap authenticates with Vault by passing username/password pair using
the LDAP authentication method</p>
</td>
</tr>
<tr>
<td>
<code>jwt</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultJwtAuth">
VaultJwtAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Jwt authenticates with Vault by passing role and JWT token using the
JWT/OIDC authentication method</p>
</td>
</tr>
<tr>
<td>
<code>cert</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultCertAuth">
VaultCertAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Cert authenticates with TLS Certificates by passing client certificate, private key and ca certificate
Cert authentication method</p>
</td>
</tr>
<tr>
<td>
<code>iam</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultIamAuth">
VaultIamAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Iam authenticates with vault by passing a special AWS request signed with AWS IAM credentials
AWS IAM authentication method</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultAwsAuth">VaultAwsAuth
</h3>
<p>
<p>VaultAwsAuth tells the controller how to do authentication with aws.
Only one of secretRef or jwt can be specified.
if none is specified the controller will try to load credentials from its own service account assuming it is IRSA enabled.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultAwsAuthSecretRef">
VaultAwsAuthSecretRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>jwt</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultAwsJWTAuth">
VaultAwsJWTAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultAwsAuthSecretRef">VaultAwsAuthSecretRef
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultAwsAuth">VaultAwsAuth</a>, 
<a href="#external-secrets.io/v1beta1.VaultIamAuth">VaultIamAuth</a>)
</p>
<p>
<p>VaultAWSAuthSecretRef holds secret references for AWS credentials
both AccessKeyID and SecretAccessKey must be defined in order to properly authenticate.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>accessKeyIDSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The AccessKeyID is used for authentication</p>
</td>
</tr>
<tr>
<td>
<code>secretAccessKeySecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The SecretAccessKey is used for authentication</p>
</td>
</tr>
<tr>
<td>
<code>sessionTokenSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>The SessionToken used for authentication
This must be defined if AccessKeyID and SecretAccessKey are temporary credentials
see: <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html">https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html</a></p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultAwsJWTAuth">VaultAwsJWTAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultAwsAuth">VaultAwsAuth</a>, 
<a href="#external-secrets.io/v1beta1.VaultIamAuth">VaultIamAuth</a>)
</p>
<p>
<p>Authenticate against AWS using service account tokens.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>serviceAccountRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#ServiceAccountSelector">
External Secrets meta/v1.ServiceAccountSelector
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultCertAuth">VaultCertAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultAuth">VaultAuth</a>)
</p>
<p>
<p>VaultJwtAuth authenticates with Vault using the JWT/OIDC authentication
method, with the role name and token stored in a Kubernetes Secret resource.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>clientCert</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ClientCert is a certificate to authenticate using the Cert Vault
authentication method</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>SecretRef to a key in a Secret resource containing client private key to
authenticate with Vault using the Cert authentication method</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultIamAuth">VaultIamAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultAuth">VaultAuth</a>)
</p>
<p>
<p>VaultIamAuth authenticates with Vault using the Vault&rsquo;s AWS IAM authentication method. Refer: <a href="https://developer.hashicorp.com/vault/docs/auth/aws">https://developer.hashicorp.com/vault/docs/auth/aws</a></p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>path</code></br>
<em>
string
</em>
</td>
<td>
<p>Path where the AWS auth method is enabled in Vault, e.g: &ldquo;aws&rdquo;</p>
</td>
</tr>
<tr>
<td>
<code>region</code></br>
<em>
string
</em>
</td>
<td>
<p>AWS region</p>
</td>
</tr>
<tr>
<td>
<code>role</code></br>
<em>
string
</em>
</td>
<td>
<p>This is the AWS role to be assumed before talking to vault</p>
</td>
</tr>
<tr>
<td>
<code>vaultRole</code></br>
<em>
string
</em>
</td>
<td>
<p>Vault Role. In vault, a role describes an identity with a set of permissions, groups, or policies you want to attach a user of the secrets engine</p>
</td>
</tr>
<tr>
<td>
<code>externalID</code></br>
<em>
string
</em>
</td>
<td>
<p>AWS External ID set on assumed IAM roles</p>
</td>
</tr>
<tr>
<td>
<code>vaultAwsIamServerID</code></br>
<em>
string
</em>
</td>
<td>
<p>X-Vault-AWS-IAM-Server-ID is an additional header used by Vault IAM auth method to mitigate against different types of replay attacks. More details here: <a href="https://developer.hashicorp.com/vault/docs/auth/aws">https://developer.hashicorp.com/vault/docs/auth/aws</a></p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultAwsAuthSecretRef">
VaultAwsAuthSecretRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specify credentials in a Secret object</p>
</td>
</tr>
<tr>
<td>
<code>jwt</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultAwsJWTAuth">
VaultAwsJWTAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specify a service account with IRSA enabled</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultJwtAuth">VaultJwtAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultAuth">VaultAuth</a>)
</p>
<p>
<p>VaultJwtAuth authenticates with Vault using the JWT/OIDC authentication
method, with the role name and a token stored in a Kubernetes Secret resource or
a Kubernetes service account token retrieved via <code>TokenRequest</code>.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>path</code></br>
<em>
string
</em>
</td>
<td>
<p>Path where the JWT authentication backend is mounted
in Vault, e.g: &ldquo;jwt&rdquo;</p>
</td>
</tr>
<tr>
<td>
<code>role</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Role is a JWT role to authenticate using the JWT/OIDC Vault
authentication method</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional SecretRef that refers to a key in a Secret resource containing JWT token to
authenticate with Vault using the JWT/OIDC authentication method.</p>
</td>
</tr>
<tr>
<td>
<code>kubernetesServiceAccountToken</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultKubernetesServiceAccountTokenAuth">
VaultKubernetesServiceAccountTokenAuth
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional ServiceAccountToken specifies the Kubernetes service account for which to request
a token for with the <code>TokenRequest</code> API.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultKVStoreVersion">VaultKVStoreVersion
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultProvider">VaultProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;v1&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;v2&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultKubernetesAuth">VaultKubernetesAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultAuth">VaultAuth</a>)
</p>
<p>
<p>Authenticate against Vault using a Kubernetes ServiceAccount token stored in
a Secret.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>mountPath</code></br>
<em>
string
</em>
</td>
<td>
<p>Path where the Kubernetes authentication backend is mounted in Vault, e.g:
&ldquo;kubernetes&rdquo;</p>
</td>
</tr>
<tr>
<td>
<code>serviceAccountRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#ServiceAccountSelector">
External Secrets meta/v1.ServiceAccountSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional service account field containing the name of a kubernetes ServiceAccount.
If the service account is specified, the service account secret token JWT will be used
for authenticating with Vault. If the service account selector is not supplied,
the secretRef will be used instead.</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional secret field containing a Kubernetes ServiceAccount JWT used
for authenticating with Vault. If a name is specified without a key,
<code>token</code> is the default. If one is not specified, the one bound to
the controller will be used.</p>
</td>
</tr>
<tr>
<td>
<code>role</code></br>
<em>
string
</em>
</td>
<td>
<p>A required field containing the Vault Role to assume. A Role binds a
Kubernetes ServiceAccount with a set of Vault policies.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultKubernetesServiceAccountTokenAuth">VaultKubernetesServiceAccountTokenAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultJwtAuth">VaultJwtAuth</a>)
</p>
<p>
<p>VaultKubernetesServiceAccountTokenAuth authenticates with Vault using a temporary
Kubernetes service account token retrieved by the <code>TokenRequest</code> API.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>serviceAccountRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#ServiceAccountSelector">
External Secrets meta/v1.ServiceAccountSelector
</a>
</em>
</td>
<td>
<p>Service account field containing the name of a kubernetes ServiceAccount.</p>
</td>
</tr>
<tr>
<td>
<code>audiences</code></br>
<em>
[]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional audiences field that will be used to request a temporary Kubernetes service
account token for the service account referenced by <code>serviceAccountRef</code>.
Defaults to a single audience <code>vault</code> it not specified.
Deprecated: use serviceAccountRef.Audiences instead</p>
</td>
</tr>
<tr>
<td>
<code>expirationSeconds</code></br>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional expiration time in seconds that will be used to request a temporary
Kubernetes service account token for the service account referenced by
<code>serviceAccountRef</code>.
Deprecated: this will be removed in the future.
Defaults to 10 minutes.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultLdapAuth">VaultLdapAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.VaultAuth">VaultAuth</a>)
</p>
<p>
<p>VaultLdapAuth authenticates with Vault using the LDAP authentication method,
with the username and password stored in a Kubernetes Secret resource.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>path</code></br>
<em>
string
</em>
</td>
<td>
<p>Path where the LDAP authentication backend is mounted
in Vault, e.g: &ldquo;ldap&rdquo;</p>
</td>
</tr>
<tr>
<td>
<code>username</code></br>
<em>
string
</em>
</td>
<td>
<p>Username is a LDAP user name used to authenticate using the LDAP Vault
authentication method</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>SecretRef to a key in a Secret resource containing password for the LDAP
user used to authenticate with Vault using the LDAP authentication
method</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.VaultProvider">VaultProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>Configures an store to sync secrets using a HashiCorp Vault
KV backend.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultAuth">
VaultAuth
</a>
</em>
</td>
<td>
<p>Auth configures how secret-manager authenticates with the Vault server.</p>
</td>
</tr>
<tr>
<td>
<code>server</code></br>
<em>
string
</em>
</td>
<td>
<p>Server is the connection address for the Vault server, e.g: &ldquo;<a href="https://vault.example.com:8200&quot;">https://vault.example.com:8200&rdquo;</a>.</p>
</td>
</tr>
<tr>
<td>
<code>path</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Path is the mount path of the Vault KV backend endpoint, e.g:
&ldquo;secret&rdquo;. The v2 KV secret engine version specific &ldquo;/data&rdquo; path suffix
for fetching secrets from Vault is optional and will be appended
if not present in specified path.</p>
</td>
</tr>
<tr>
<td>
<code>version</code></br>
<em>
<a href="#external-secrets.io/v1beta1.VaultKVStoreVersion">
VaultKVStoreVersion
</a>
</em>
</td>
<td>
<p>Version is the Vault KV secret engine version. This can be either &ldquo;v1&rdquo; or
&ldquo;v2&rdquo;. Version defaults to &ldquo;v2&rdquo;.</p>
</td>
</tr>
<tr>
<td>
<code>namespace</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Name of the vault namespace. Namespaces is a set of features within Vault Enterprise that allows
Vault environments to support Secure Multi-tenancy. e.g: &ldquo;ns1&rdquo;.
More about namespaces can be found here <a href="https://www.vaultproject.io/docs/enterprise/namespaces">https://www.vaultproject.io/docs/enterprise/namespaces</a></p>
</td>
</tr>
<tr>
<td>
<code>caBundle</code></br>
<em>
[]byte
</em>
</td>
<td>
<em>(Optional)</em>
<p>PEM encoded CA bundle used to validate Vault server certificate. Only used
if the Server URL is using HTTPS protocol. This parameter is ignored for
plain HTTP protocol connection. If not set the system root certificates
are used to validate the TLS connection.</p>
</td>
</tr>
<tr>
<td>
<code>caProvider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.CAProvider">
CAProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The provider for the CA bundle to use to validate Vault server certificate.</p>
</td>
</tr>
<tr>
<td>
<code>readYourWrites</code></br>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>ReadYourWrites ensures isolated read-after-write semantics by
providing discovered cluster replication states in each request.
More information about eventual consistency in Vault can be found here
<a href="https://www.vaultproject.io/docs/enterprise/consistency">https://www.vaultproject.io/docs/enterprise/consistency</a></p>
</td>
</tr>
<tr>
<td>
<code>forwardInconsistent</code></br>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>ForwardInconsistent tells Vault to forward read-after-write requests to the Vault
leader instead of simply retrying within a loop. This can increase performance if
the option is enabled serverside.
<a href="https://www.vaultproject.io/docs/configuration/replication#allow_forwarding_via_header">https://www.vaultproject.io/docs/configuration/replication#allow_forwarding_via_header</a></p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.WebhookCAProvider">WebhookCAProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.WebhookProvider">WebhookProvider</a>)
</p>
<p>
<p>Defines a location to fetch the cert for the webhook provider from.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code></br>
<em>
<a href="#external-secrets.io/v1beta1.WebhookCAProviderType">
WebhookCAProviderType
</a>
</em>
</td>
<td>
<p>The type of provider to use such as &ldquo;Secret&rdquo;, or &ldquo;ConfigMap&rdquo;.</p>
</td>
</tr>
<tr>
<td>
<code>name</code></br>
<em>
string
</em>
</td>
<td>
<p>The name of the object located at the provider type.</p>
</td>
</tr>
<tr>
<td>
<code>key</code></br>
<em>
string
</em>
</td>
<td>
<p>The key the value inside of the provider type to use, only used with &ldquo;Secret&rdquo; type</p>
</td>
</tr>
<tr>
<td>
<code>namespace</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>The namespace the Provider type is in.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.WebhookCAProviderType">WebhookCAProviderType
(<code>string</code> alias)</p></h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.WebhookCAProvider">WebhookCAProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;ConfigMap&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;Secret&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="external-secrets.io/v1beta1.WebhookProvider">WebhookProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>AkeylessProvider Configures an store to sync secrets using Akeyless KV.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>method</code></br>
<em>
string
</em>
</td>
<td>
<p>Webhook Method</p>
</td>
</tr>
<tr>
<td>
<code>url</code></br>
<em>
string
</em>
</td>
<td>
<p>Webhook url to call</p>
</td>
</tr>
<tr>
<td>
<code>headers</code></br>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Headers</p>
</td>
</tr>
<tr>
<td>
<code>body</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Body</p>
</td>
</tr>
<tr>
<td>
<code>timeout</code></br>
<em>
<a href="https://pkg.go.dev/k8s.io/apimachinery/pkg/apis/meta/v1#Duration">
Kubernetes meta/v1.Duration
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Timeout</p>
</td>
</tr>
<tr>
<td>
<code>result</code></br>
<em>
<a href="#external-secrets.io/v1beta1.WebhookResult">
WebhookResult
</a>
</em>
</td>
<td>
<p>Result formatting</p>
</td>
</tr>
<tr>
<td>
<code>secrets</code></br>
<em>
<a href="#external-secrets.io/v1beta1.WebhookSecret">
[]WebhookSecret
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Secrets to fill in templates
These secrets will be passed to the templating function as key value pairs under the given name</p>
</td>
</tr>
<tr>
<td>
<code>caBundle</code></br>
<em>
[]byte
</em>
</td>
<td>
<em>(Optional)</em>
<p>PEM encoded CA bundle used to validate webhook server certificate. Only used
if the Server URL is using HTTPS protocol. This parameter is ignored for
plain HTTP protocol connection. If not set the system root certificates
are used to validate the TLS connection.</p>
</td>
</tr>
<tr>
<td>
<code>caProvider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.WebhookCAProvider">
WebhookCAProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The provider for the CA bundle to use to validate webhook server certificate.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.WebhookResult">WebhookResult
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.WebhookProvider">WebhookProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>jsonPath</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Json path of return value</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.WebhookSecret">WebhookSecret
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.WebhookProvider">WebhookProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>name</code></br>
<em>
string
</em>
</td>
<td>
<p>Name of this secret in templates</p>
</td>
</tr>
<tr>
<td>
<code>secretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<p>Secret ref to fill in credentials</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.YandexCertificateManagerAuth">YandexCertificateManagerAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.YandexCertificateManagerProvider">YandexCertificateManagerProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>authorizedKeySecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The authorized key used for authentication</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.YandexCertificateManagerCAProvider">YandexCertificateManagerCAProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.YandexCertificateManagerProvider">YandexCertificateManagerProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>certSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.YandexCertificateManagerProvider">YandexCertificateManagerProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>YandexCertificateManagerProvider Configures a store to sync secrets using the Yandex Certificate Manager provider.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>apiEndpoint</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Yandex.Cloud API endpoint (e.g. &lsquo;api.cloud.yandex.net:443&rsquo;)</p>
</td>
</tr>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.YandexCertificateManagerAuth">
YandexCertificateManagerAuth
</a>
</em>
</td>
<td>
<p>Auth defines the information necessary to authenticate against Yandex Certificate Manager</p>
</td>
</tr>
<tr>
<td>
<code>caProvider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.YandexCertificateManagerCAProvider">
YandexCertificateManagerCAProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The provider for the CA bundle to use to validate Yandex.Cloud server certificate.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.YandexLockboxAuth">YandexLockboxAuth
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.YandexLockboxProvider">YandexLockboxProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>authorizedKeySecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The authorized key used for authentication</p>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.YandexLockboxCAProvider">YandexLockboxCAProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.YandexLockboxProvider">YandexLockboxProvider</a>)
</p>
<p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>certSecretRef</code></br>
<em>
<a href="https://pkg.go.dev/github.com/external-secrets/external-secrets/apis/meta/v1#SecretKeySelector">
External Secrets meta/v1.SecretKeySelector
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="external-secrets.io/v1beta1.YandexLockboxProvider">YandexLockboxProvider
</h3>
<p>
(<em>Appears on:</em>
<a href="#external-secrets.io/v1beta1.SecretStoreProvider">SecretStoreProvider</a>)
</p>
<p>
<p>YandexLockboxProvider Configures a store to sync secrets using the Yandex Lockbox provider.</p>
</p>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>apiEndpoint</code></br>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Yandex.Cloud API endpoint (e.g. &lsquo;api.cloud.yandex.net:443&rsquo;)</p>
</td>
</tr>
<tr>
<td>
<code>auth</code></br>
<em>
<a href="#external-secrets.io/v1beta1.YandexLockboxAuth">
YandexLockboxAuth
</a>
</em>
</td>
<td>
<p>Auth defines the information necessary to authenticate against Yandex Lockbox</p>
</td>
</tr>
<tr>
<td>
<code>caProvider</code></br>
<em>
<a href="#external-secrets.io/v1beta1.YandexLockboxCAProvider">
YandexLockboxCAProvider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The provider for the CA bundle to use to validate Yandex.Cloud server certificate.</p>
</td>
</tr>
</tbody>
</table>
<hr/>
<p><em>
Generated with <code>gen-crd-api-reference-docs</code>.
</em></p>
