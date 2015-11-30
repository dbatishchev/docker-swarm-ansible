vagrant up
vagrant ssh master

ansible-playbook /vagrant/ansible/infra.yml -i /vagrant/ansible/hosts/prod
