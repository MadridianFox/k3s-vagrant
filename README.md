# K3S on vagrant with virtualbox driver #

Этот репозиторий содержит всё необходимое для того чтобы получить вирутальную машину с установленным в ней  k3s - облегчённой версией k8s.

## Установка ##

Зависимости:

- virtualbox
- vagrant
- kubectl

После клонирования репозитория заходим в папку и выпоняем:
```
vagrant up
```

Это создат виртуальную машину с именем `k3s`.
Машина пробрасывает порт 6443 на localhost для подключения через kubectl.

## Подключение ##
Для получения конфига подключения к `k3s` выполните команду:
```
ssh vagrant@localhost -p 2222 'sudo cat /etc/rancher/k3s/k3s.yaml' >> .kubeconfig
```
Далее можно настроить алиасы, для того чтобы не указывать каждый раз путь до этого конифга:
```
alias vkube='kubectl --kubeconfig=/home/$USER/machines/k3s/.kubeconfig'
alias vhelm='helm --kubeconfig=/home/$USER/machines/k3s/.kubeconfig'
```
