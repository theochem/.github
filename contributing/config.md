# Git and GitHub configuration

- If you don't already have an SSH key pair, create one using the following terminal command:

    ```bash
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f "${HOME}/.ssh/id_rsa_github_com"
    ```

    An empty passphrase is convenient and should be fine.
    This will generate a private and a public key in `${HOME}/.ssh`.

- Upload your *public* SSH key to https://github.com/settings/keys.
  This is a single long line in `${HOME}/.ssh/id_rsa_github_com.pub`,
  which you can copy and paste into the settings page in your browser.

- Configure SSH on you computer to use this key pair for authentication
  when pushing branches to GitHub.
  Add the following to your `.ssh/config` file:

    ```
    # Do not allow SSH to try all keys, as SSH servers only accept a few attempts.
    # Keys must be specified for each host.
    IdentitiesOnly yes

    Host github.com
        Hostname github.com
        ForwardX11 no
        IdentityFile %d/.ssh/id_rsa_github_com
    ```

    (Make sure you have the correct name for the *private* key file.)

- Configure Git and to use the name and email address associated with your GitHub account, by running the following commands:

    ```
    git config --global user.name "Your Name"
    git config --global user.email "youremail@yourdomain.com"
    ```

    Use your real name.
    Take the same e-mail address that you use for your (academic) affiliation.
    (You can configure your GitHub account to recognize multiple e-mail addresses.)

- Optionally, you can set more convenient defaults:

    - The default text editor for commit messages can be set to `nano` as follows:

        ```
        git config --global core.editor nano
        ```

    - There are several tools to make the output of `git diff` more readable,
      such as: [difftastic], [diffr] or [delta].

    - You can change the bash prompt to summarize the current state of the Git repository.
      This instant visual feedback, makes working with Git much more intuitive.
      There are many popular options out there:

      - [powerline], [liquidprompt], [starship] and [ohmyposh] are among the most fancy ones,
        but they have non-bash dependencies that make them a bit harder to install.

      - [powerbash] and [pureline] are pure shell implementations,
        which makes them a bit easier to set up.

[difftastic]: https://github.com/Wilfred/difftastic
[diffr]: https://github.com/mookid/diffr
[delta]: https://dandavison.github.io/delta/
[powerline]: https://github.com/powerline/powerline
[powerbash]: https://github.com/tovrstra/powerbash/tree/merged1
[starship]: https://github.com/starship/starship
[ohmyposh]: https://ohmyposh.dev/
[liquidprompt]: https://liquidprompt.readthedocs.io/
[gitstatus]: https://github.com/romkatv/gitstatus
[pureline]: https://github.com/chris-marsh/pureline
