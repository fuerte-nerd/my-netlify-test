# Netlify CMS with Gatsby (Step-by-Step)

1. Create project
```bash
gatsby new nameOfProject
```

2. Navigate into directory and install dependencies
```bash
cd nameOfProject
npm i netlify-cms-app gatsby-plugin-netlify-cms
```

3. Update gatsby-config.js to load CMS plugin
```javascript
    module.exports = {
        plugins: [`gatsby-plugin-netlify-cms`]
    }
```

4. Create a `static` directory with an `admin` subdirectory in the project root
```bash
mkdir static
cd static
mkdir admin
```

5. Create a `config.yml` file in the newly-created admin folder
```
touch config.yml
```

6. Add the following code to the `config.yml` file
```yml
backend:
  name: git-gateway
  branch: master
media_folder: static/assets
public_folder: assets
collections:
  - name: blog
    label: Blog
    folder: blog
    create: true
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}"
    editor:
      preview: false
    fields:
      - { name: path, label: Path }
      - { name: featured_image, label: Image, widget: image }
      - { name: date, label: Date, widget: datetime }
      - { name: title, label: Title }
      - { name: body, label: Body, widget: markdown }
```

