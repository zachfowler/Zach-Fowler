## Solution Guide: Securing `root`

In this final activity, you worked as a junior administrator to make your final changes to the system. 

The senior administrator asked that you secure the root account to prevent attackers from logging in as `root`.

To complete this activity, you needed to:

- Create a strong password for root.

- Lock the root account.

- Ensure that the root account doesn't have a login shell.

- Ensure that the root account cannot be assigned a `tty` terminal.

- Ensure that a user cannot login directly as root.

- Ensure that the bootloader has a password.


The first step is changing `root`'s password.

- Run `sudo passwd root` to change root's password to `1RuT3ZLg05`.

To lock the root account.

- Run `sudo usermod -L root`

Change the login shell on the root account to prevent a login.

- Run `sudo usermod -s /usr/sbin/nologin root`

Verify that you cannot log in with `root`.

- Run  `sudo su root`

- You should get an authentication error.

Now, secure the boot loader.

- Run `sudo nano /etc/grub.d/40_custom` to edit the file.

- Add `set superusers="root"`

- Add `password root 2XuTeZig0$`

- Your output should look like:

  ```bash
  #!/bin/sh
  exec tail -n +3 $0
  # This file provides an easy way to add custom menu entries.  Simply type the
  # menu entries you want to add after this comment.  Be careful not to change
  # the 'exec tail' line above.
  set superusers="root"
  password root 2XuTeZig0$
  ```

- Save the file with `ctrl + x`, `y`, and `enter`.

- Run `sudo update-grub` to update the configuration.

Now, create a hash of the password.

- Run `sudo grub-mkpasswd-pbkdf2`

- Enter `2XuTeZig0$` to get the password hash:

  ```bash
  grub.pbkdf2.sha512.10000.343B37A531EEDB03DC65DE6A0F1D1D2E0D00BF3CBBC3BB093EE6D03C7CA8F080985BE622E3C90840E6AB1F85789983A8E673A5684C18A0B213143AE2D1014EAD.AFBBC19D6737EC1DF7D6465DDD07F2E20A8A9A1234AA3083133B3960F394104801C089875B54B02798BF253044C539EA6842FE576429189F1DB5E53152DA942C
  ```

Run `sudo nano /etc/grub.d/40_custom` to edit the file.

- Add `set superusers="root"`

- Add `password root grub.pbkdf2.sha512.10000.343B37A531EEDB03DC65DE6A0F1D1D2E0D00BF3CBBC3BB093EE6D03C7CA8F080985BE622E3C90840E6AB1F85789983A8E673A5684C18A0B213143AE2D1014EAD.AFBBC19D6737EC1DF7D6465DDD07F2E20A8A9A1234AA3083133B3960F394104801C089875B54B02798BF253044C539EA6842FE576429189F1DB5E53152DA942C`

Your file should look like:

```bash
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
set superusers="root"
password root grub.pbkdf2.sha512.10000.343B37A531EEDB03DC65DE6A0F1D1D2E0D00BF3CBBC3BB093EE6D03C7CA8F080985BE622E3C90840E6AB1F85789983A8E673A5684C18A0B213143AE2D1014EAD.AFBBC19D6737EC1DF7D6465DDD07F2E20A8A9A1234AA3083133B3960F394104801C089875B54B02798BF253044C539EA6842FE576429189F1DB5E53152DA942C
```

- Save the file with `ctrl + x`, `y`, and `enter`.

- Run `sudo update-grub` to update the configuration. 