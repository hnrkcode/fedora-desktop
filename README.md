# Fedora Desktop Configuration

```bash
sudo dnf upgrade --refresh -y
sudo dnf install -y ansible
```

```bash
ansible-playbook site.yml --list-tasks
```

```bash
ansible-playbook site.yml --check --diff
```

```bash
ansible-playbook site.yml
```