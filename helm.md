
brew install helm
helm repo add stable https://kubernetes-charts.storage.googleapis.com/
helm repo update 
helm install stable/mysql --generate-name OR helm install nanhe-mysql stable/mysql
helm ls
helm uninstall mysql-1585638172
helm get -h
helm status mysql-1585638172
helm show values stable/mariadb
echo '{mariadbUser: user0, mariadbDatabase: user0db}' > config.yaml
helm install -f config.yaml stable/mariadb --generate-name

helm get values mysql-1585638172
