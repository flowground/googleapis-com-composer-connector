# ![LOGO](logo.png) Cloud Composer **flow**ground Connector

## Description

A generated **flow**ground connector for the Cloud Composer API (version v1).

Generated from: https://api.apis.guru/v2/specs/googleapis.com/composer/v1/swagger.json<br/>
Generated at: 2019-05-07T17:41:22+03:00

## API Description

Manages Apache Airflow environments on Google Cloud Platform.

## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### Deletes a long-running operation. This method indicates that the client is<br/>
> no longer interested in the operation result. It does not cancel the<br/>
> operation. If the server doesn't support this method, it returns<br/>
> `google.rpc.Code.UNIMPLEMENTED`.

*Tags:* `projects`

#### Input Parameters
* `name` - _required_ - The name of the operation resource to be deleted.
* `access_token` - _optional_ - OAuth access token.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Gets the latest state of a long-running operation.  Clients can use this<br/>
> method to poll the operation result at intervals as recommended by the API<br/>
> service.

*Tags:* `projects`

#### Input Parameters
* `name` - _required_ - The name of the operation resource.
* `access_token` - _optional_ - OAuth access token.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Update an environment.

*Tags:* `projects`

#### Input Parameters
* `name` - _required_ - The relative resource name of the environment to update, in the form:
"projects/{projectId}/locations/{locationId}/environments/{environmentId}"
* `updateMask` - _optional_ - Required. A comma-separated list of paths, relative to `Environment`, of
fields to update.
For example, to set the version of scikit-learn to install in the
environment to 0.19.0 and to remove an existing installation of
numpy, the `updateMask` parameter would include the following two
`paths` values: "config.softwareConfig.pypiPackages.scikit-learn" and
"config.softwareConfig.pypiPackages.numpy". The included patch
environment would specify the scikit-learn version as follows:

    {
      "config":{
        "softwareConfig":{
          "pypiPackages":{
            "scikit-learn":"==0.19.0"
          }
        }
      }
    }

Note that in the above example, any existing PyPI packages
other than scikit-learn and numpy will be unaffected.

Only one update type may be included in a single request's `updateMask`.
For example, one cannot update both the PyPI packages and
labels in the same request. However, it is possible to update multiple
members of a map field simultaneously in the same request. For example,
to set the labels "label1" and "label2" while clearing "label3" (assuming
it already exists), one can
provide the paths "labels.label1", "labels.label2", and "labels.label3"
and populate the patch environment as follows:

    {
      "labels":{
        "label1":"new-label1-value"
        "label2":"new-label2-value"
      }
    }

Note that in the above example, any existing labels that are not
included in the `updateMask` will be unaffected.

It is also possible to replace an entire map field by providing the
map field's path in the `updateMask`. The new value of the field will
be that which is provided in the patch environment. For example, to
delete all pre-existing user-specified PyPI packages and
install botocore at version 1.7.14, the `updateMask` would contain
the path "config.softwareConfig.pypiPackages", and
the patch environment would be the following:

    {
      "config":{
        "softwareConfig":{
          "pypiPackages":{
            "botocore":"==1.7.14"
          }
        }
      }
    }

**Note:** Only the following fields can be updated:

 <table>
 <tbody>
 <tr>
 <td><strong>Mask</strong></td>
 <td><strong>Purpose</strong></td>
 </tr>
 <tr>
 <td>config.softwareConfig.pypiPackages
 </td>
 <td>Replace all custom custom PyPI packages. If a replacement
 package map is not included in `environment`, all custom
 PyPI packages are cleared. It is an error to provide both this mask and a
 mask specifying an individual package.</td>
 </tr>
 <tr>
 <td>config.softwareConfig.pypiPackages.<var>packagename</var></td>
 <td>Update the custom PyPI package <var>packagename</var>,
 preserving other packages. To delete the package, include it in
 `updateMask`, and omit the mapping for it in
 `environment.config.softwareConfig.pypiPackages`. It is an error
 to provide both a mask of this form and the
 "config.softwareConfig.pypiPackages" mask.</td>
 </tr>
 <tr>
 <td>labels</td>
 <td>Replace all environment labels. If a replacement labels map is not
 included in `environment`, all labels are cleared. It is an error to
 provide both this mask and a mask specifying one or more individual
 labels.</td>
 </tr>
 <tr>
 <td>labels.<var>labelName</var></td>
 <td>Set the label named <var>labelName</var>, while preserving other
 labels. To delete the label, include it in `updateMask` and omit its
 mapping in `environment.labels`. It is an error to provide both a
 mask of this form and the "labels" mask.</td>
 </tr>
 <tr>
 <td>config.nodeCount</td>
 <td>Horizontally scale the number of nodes in the environment. An integer
 greater than or equal to 3 must be provided in the `config.nodeCount` field.
 </td>
 </tr>
 <tr>
 <td>config.softwareConfig.airflowConfigOverrides</td>
 <td>Replace all Apache Airflow config overrides. If a replacement config
 overrides map is not included in `environment`, all config overrides
 are cleared.
 It is an error to provide both this mask and a mask specifying one or
 more individual config overrides.</td>
 </tr>
 <tr>
 <td>config.softwareConfig.airflowConfigOverrides.<var>section</var>-<var>name
 </var></td>
 <td>Override the Apache Airflow config property <var>name</var> in the
 section named <var>section</var>, preserving other properties. To delete
 the property override, include it in `updateMask` and omit its mapping
 in `environment.config.softwareConfig.airflowConfigOverrides`.
 It is an error to provide both a mask of this form and the
 "config.softwareConfig.airflowConfigOverrides" mask.</td>
 </tr>
 <tr>
 <td>config.softwareConfig.envVariables</td>
 <td>Replace all environment variables. If a replacement environment
 variable map is not included in `environment`, all custom environment
 variables  are cleared.
 It is an error to provide both this mask and a mask specifying one or
 more individual environment variables.</td>
 </tr>
 </tbody>
 </table>
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Lists operations that match the specified filter in the request. If the<br/>
> server doesn't support this method, it returns `UNIMPLEMENTED`.<br/>
> <br/>
> NOTE: the `name` binding allows API services to override the binding<br/>
> to use different resource name schemes, such as `users/*/operations`. To<br/>
> override the binding, API services can add a binding such as<br/>
> `"/v1/{name=users/*}/operations"` to their service configuration.<br/>
> For backwards compatibility, the default name includes the operations<br/>
> collection id, however overriding users must ensure the name binding<br/>
> is the parent resource, without the operations collection id.

*Tags:* `projects`

#### Input Parameters
* `filter` - _optional_ - The standard list filter.
* `name` - _required_ - The name of the operation's parent resource.
* `pageSize` - _optional_ - The standard list page size.
* `pageToken` - _optional_ - The standard list page token.
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### List environments.

*Tags:* `projects`

#### Input Parameters
* `pageSize` - _optional_ - The maximum number of environments to return.
* `pageToken` - _optional_ - The next_page_token value returned from a previous List request, if any.
* `parent` - _required_ - List environments in the given project and location, in the form:
"projects/{projectId}/locations/{locationId}"
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Create a new environment.

*Tags:* `projects`

#### Input Parameters
* `parent` - _required_ - The parent must be of the form "projects/{projectId}/locations/{locationId}".
* `access_token` - _optional_ - OAuth access token.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### List ImageVersions for provided location.

*Tags:* `projects`

#### Input Parameters
* `pageSize` - _optional_ - The maximum number of image_versions to return.
* `pageToken` - _optional_ - The next_page_token value returned from a previous List request, if any.
* `parent` - _required_ - List ImageVersions in the given project and location, in the form:
"projects/{projectId}/locations/{locationId}"
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

## License

**flow**ground :- Telekom iPaaS / googleapis-com-composer-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
