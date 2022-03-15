# 17032022-examen
# Enlaces de interes
## Para aprobar si hay suerte

repasar pushear cambios al repo en github, que lo vamos a hacer añadiendo todos los scripts seguidos en README.md, el código de los scripts es:
https://gist.github.com/repositorioinformatico/077b29bc25f8b48d492afd4d79cfac31
>
```sh
mkdir 17
cd 17
touch f1
git add f1
git commit -m "c 1 en master"
touch f2
git add f2
git commit -m "c 2 en master"
git checkout -b feature
git checkout master
touch f3
git add f3
git commit -m "c 3 en master"
git --no-pager log --oneline --graph
git checkout feature
touch change1
git add change1
git commit -m "c 1 en feature"
touch change2
git add change2
git commit -m "c 2 en feature"
git --no-pager log --oneline --graph
git --no-pager log --oneline --graph --all
git checkout master
git merge feature
git --no-pager log --oneline --graph --all
```

https://gist.github.com/repositorioinformatico/6bca63d10f66ad6ee38e8320f1cbb70c
```sh
mkdir 17
cd 17
touch f1
git add f1
git commit -m "c 1 en master"
touch f2
git add f2
git commit -m "c 2 en master"
git checkout -b feature
git checkout master
touch f3
git add f3
git commit -m "c 3 en master"
git --no-pager log --oneline --graph
git checkout feature
touch change1
git add change1
git commit -m "c 1 en feature"
touch change2
git add change2
git commit -m "c 2 en feature"
git rebase master #esto aplana el historial pero los dos commits de la rama feature pasarán a tener otro hash!
git checkout master
git merge feature

```

https://gist.github.com/repositorioinformatico/cd7d99aef5ce9b4b642983cd1bc532d6
```sh
#!/usr/bin/env bash
git init
touch f1
git add f1
git commit -m "c 1 en master"
touch f2
git add f2
git commit -m "c 2 en master"
git checkout -b feature
git checkout master
touch f3
git add f3
git commit -m "c 3 en master"
git --no-pager log --oneline --graph
git checkout feature
touch change1
git add change1
git commit -m "c 1 en feature"
touch change2
git add change2
git commit -m "c 2 en feature"
git --no-pager log --oneline --graph
#hasta aquí, con esta estructura del repo, ahora podremos entender el rebase y compararlo con el merge
```

https://gist.github.com/repositorioinformatico/34d48855c55e098b42a96728a7985fd2
```sh
#!/usr/bin/env bash
git init
touch f1
git add f1
git commit -m "f1"
touch f2
git add f2
git commit -m "f2"
touch f3
git add f3
git commit -m "f3-este-commit-rompe"
touch f4
git add f4
git commit -m "f4-este-commit-rompe"
touch f5
git add f5
git commit -m "f5"
git --no-pager log --oneline --all 
#hasta aqui
git rebase --interactive <commit-antes-de-lo-que-queremos-borrar>
#cambiar 'pick' por 'drop'
```

https://gist.github.com/repositorioinformatico/e13be768677dedc7e3cc6d48383e45c7
```sh
name: GitHub Actions Demo
on: 
  push:
      branches: [ main ]
jobs:
  Explore-GitHub-Actions:
    runs-on: ubuntu-latest
    steps:
      - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event."
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."
      - name: Check out repository code
        uses: actions/checkout@v2
      - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner."
      - run: echo "🖥️ The workflow is now ready to test your code on the runner."
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}
      - name: Que ruta es
        run: pwd
      - run: echo "🍏 This job's status is ${{ job.status }}."
```

https://gist.github.com/repositorioinformatico/0c17fb883ecdbce7fe767d014e7ca3a4
```sh
cd repository
git checkout --orphan orphan_name
git rm -rf .
rm '.gitignore'
echo "#Title of Readme" > README.md
git add README.md
git commit -a -m "Initial Commit"
git push origin orphan_name
```

https://gist.github.com/repositorioinformatico/cc2b0fbd413b5970dc73afba2e75cba2
```sh
#EXPLICACIÓN: Si solo una rama modifica un fichero, al
#mergear, esos cambios serán aceptados sin conflicto
rm -rf .git
rm f1
git init
echo "L1 en f1 en rama main" >> f1
git add f1
git commit -m "+f1:L1"
echo "L2 en f1 en rama main" >> f1
git add f1
git commit -m "+f1:L2"
git --no-pager log --oneline --all --graph
git checkout -b rama1
echo "L1 en f1 en rama1" >> f1
git add f1
git commit -m "+f1:L1"
echo "L2 en f1 en rama1" >> f1
git add f1
git commit -m "+f1:L2"
git checkout main
sed -i s/$/MOD/ f1
cat f1
git add f1
git commit -m "+f1:L1:L2:+MOD"
git merge --no-ff --no-edit rama1
git --no-pager log --oneline --all --graph
cat f1

```





