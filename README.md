  GNU nano 5.9                      README.md *                              
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
