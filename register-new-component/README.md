# Register New Component Template

## Outline

The template allows for quickly and efficiently registering a repository to the Backstage catalog by adding and configuring the `catalog-info.yaml` with the recommended data points necessary for the entity to be listed in the catalog, as well as enabling TechDocs. Optionally, you are able to configure additional integrations such as ArgoCD or Pager Duty.

## Inputs

1. Collect component information:
   - Name: The name of the component we are registering, this will be parsed and converted into a human readable title.
   - Description: This should be used to provided detailed information in the catalog list.
2. Collect component location:
   - Repo Host: Hardcoded and hidden, this is used in building the pull request. Alternatively, you may expose this as a select list [example below].
   - Repo Name: The name of the repository to be registered in Backstage. The list is populated through the Backstage GitHub integration.
3. Collect integration configuration data:
   - Configuration Values: Set the integration specific information, such as App Names or Service Id's.
   - TechDocs Path: Set the directory path to be used. The Default is `docs:.`, but `url:{url}` is supported.

Repo Host Example:

```
   repoUrl:
      title: Repository Location
      type: string
      ui:field: RepoUrlPicker
      ui:options:
        allowedHosts:
          - github.com
```

## Outputs

- Creates a pull request to add the following additions to the repository:
  1. Creates the `catalog-info.yaml` file for registration in the catalog.
     - Conditionally: Enables any integrations if necessary data is provided.
  2. Creates the required files for TechDocs if `Enable TechDocs` is checked:
     - `MKDocs.yaml`: The configuration file for the repositories TechDocs.
     - `/docs/index.md`: The index page for the repositories TechDocs.

## TODO's

### GitHub Proxy

- [ ] In GitHub, navigate to `Settings > Developer Settings > Personal access tokens > Tokens (classic)`. Press **Generate new token Classic**.
- [ ] Configure the GitHub token in your Backstage configuration under integrations.github.

### Template Details

- [ ] `Spec > Owner`: Set the owner, most commonly the same person/group who owns the template.

### Component Details

- [ ] `type`: Confirm the `default` and the types available are options you support.
- [ ] `lifecycle`: Confirm the `default` and the lifecycles available are options you support.
- [ ] `owner`: Will the component be owned by an individual, group or both?

### Component Location

- [ ] `repoOrg`: Set your GitHub organization name.

### Integrations

- [ ] `properties`: Configure a property for each integration you would like to support enablement at registrations here.
