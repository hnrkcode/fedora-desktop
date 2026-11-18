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

## Personal configuration

Run the playbook as your desktop user, not with `sudo`; individual system tasks
request privilege escalation when needed.

### Git

Existing Git configuration is preserved. By default, the playbook leaves your
Git identity unchanged. To manage it explicitly, pass either or both variables:

```bash
ansible-playbook site.yml -e '{"git_user_name": "Your Name", "git_user_email": "you@example.com"}'
```

Only the supplied, nonempty identity settings are updated in `~/.gitconfig`;
aliases, signing settings, includes, and other configuration are retained.
Omitted or empty variables leave the corresponding setting unchanged. On a new
machine, configure your identity before making commits.

### Zsh

The playbook manages `~/.zshrc`. Before replacing an existing file with different
contents, it saves a timestamped backup alongside it (`~/.zshrc.*~`). Unchanged
runs do not create additional backups.

Put personal aliases, environment variables, and other overrides in
`~/.zshrc.local`. This optional file is sourced last and is never modified by the
playbook. When adopting this configuration, move the personal settings you want
to keep from your old `.zshrc` or its backup into `.zshrc.local`.
