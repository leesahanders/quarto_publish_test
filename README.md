# Quarto With the Jupyter Engine

## Deploy

Steps: 

* Test locally
* Acquire an [API key](https://docs.rstudio.com/connect/user/api-keys/) 
* Publish with your method of choice 

Tip: Use [quarto projects](https://quarto.org/docs/projects/quarto-projects.html) for the most robust publishing experience. The rsconnect-python package (and git backed publishing on Connect) as of 2022/11/07 do not have support for publishing standalone documents and needs quarto content to be in a project. 

**Quarto CLI**

```bash
quarto publish connect quarto-python-lightbox.qmd
```

**rsconnect-python**

Configure your server address: 
```
rsconnect add \
    --api-key <MY-API-KEY> \
    --server <https://connect.example.org:3939> \
    --name <SERVER-NICKNAME>
```

Create the requirements file: 
```
python -m pip freeze > requirements.txt
```

Publish: 
```
rsconnect deploy quarto . -n <SERVER-NICKNAME>
```

[Important: If your Quarto content contains R code, you cannot use the rsconnect-python CLI's rsconnect deploy quarto function. You can still use rsconnect deploy manifest to deploy content for which a manifest has already been generated.](https://quarto.org/docs/publishing/rstudio-connect.html) Instead use [rsconnect](https://github.com/rstudio/rsconnect). 

**git-backed**

Writing the manifest file: 

```bash
rsconnect write-manifest quarto .
```

## Resources

- [RStudio Connect User Guide - Quarto (Python)](https://docs.rstudio.com/connect/user/publishing-cli-quarto/)
- [quarto cli](https://quarto.org/docs/publishing/rstudio-connect.html)
- [rsconnect](https://github.com/rstudio/rsconnect)
- [rsconnect-python](https://github.com/rstudio/rsconnect-python)
- [quarto projects](https://quarto.org/docs/projects/quarto-projects.html)
- [RStudio Connect User Guide - Git Backed Publishing ](https://docs.rstudio.com/connect/user/git-backed/)
- [Quarto Version Manager](https://github.com/dpastoor/qvm)
- [Lightbox Quarto Extension](https://github.com/quarto-ext/lightbox)
