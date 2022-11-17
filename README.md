# AzureDevOps.Automation.Pipeline.Configuration.v2

> Application-type CI/CD pipeline blueprint configuration templates

Review our [pipeline blog series](https://wsbctechnicalblog.github.io/why-pipelines-part1.html), in particular [Meet our second-generation app-type blueprints](https://wsbctechnicalblog.github.io/yaml-pipelines-part10.html) for more information on this application-type continuous integration (CD) / continuous delivery (CD) pipeline blueprints, to empower engineering with consistent and standardized pipeline blueprints.

In this README:
- Why do we need this repository?
- What is the structure of the repository?
- What is currently in this repository?
- How does the self-service automation use the repository?

---

# Why do we need this repository?

Each instance of an application-type CI/CD blueprint pipeline has a configuration variable template, named ```<portfolio>-<product>-config.yml```. It contains configuration that is needed and passed by the ```*-control.yml``` template to the ```*-cd.yml``` continuous delivery template, such as the [Azure DevOPs Environment](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/environments?view=azure-devops) name and parameters needed by the deployment tasks.

---

# What is the structure of the repository?

The structure is simple. 

- All configuration files are stored in the **deploy** folder. 
- In our v1 blueprints the configuration templates were named ```deploy/<portfolio>-<product>-config.yml```, which resulted in a long and unmaintainable list of configuration files.
- In our v2 blueprints (**this**) the configuration templates are named ```deploy/portfolio/<product-config.yml>``` delivering a simple hierarchy, divided by portfolio.

```
    deploy
      |
      +---default.config
      |          |
      |          +--- nuget-package-config.yml
      |
      +--- <portfolio1>
      |          |
      |          +--- <product1>
      |          +--- <product2>
      |          ...
      |          +--- <product...n>
      +--- <portfolio2>
      |          |
      ...          +--- <product2>

```

---

# What is currently in this repository?

Apart from this readme, this repository contains one sample ```deploy/<portfolio>-<product>-config.yml``` configuration file, based on the ```__101__``` starter blueprint.

---

# How does the self-service automation use the repository?

Our self-service automation grabs the sample configuration template, associated with the respective application-type blueprint, and copies it to this repository using the **portfolio** and **product** names passed to our self-service automation script.

See [Self-service automation - A dream turns into reality](https://wsbctechnicalblog.github.io/yaml-pipelines-part9.html) for more details.

---

