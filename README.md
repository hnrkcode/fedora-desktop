# Fedora Desktop Configuration

```bash
sudo dnf upgrade --refresh -y
sudo dnf install -y ansible
ansible-galaxy collection install -r requirements.yml
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
