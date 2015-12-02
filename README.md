vagrant up
vagrant ssh master

ansible-playbook /vagrant/ansible/infra.yml -i /vagrant/ansible/hosts/prod

docker -H tcp://192.168.50.100:8333 ps -a
docker -H tcp://0.0.0.0:2375 ps -a


Master:


Node: