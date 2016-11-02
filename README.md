# Ansible Role: yum repos on CentOS 7

Installs well know repos (like epel, ius) or any custom repo.

## Requirements

Tested CentOS 7

## Role Variables

Available variables are listed below, along with default values `defaults/main.yml`

Define your custom repositories.

    yum_repos_list_custom: {}

Example:

    yum_repos_list_custom:
      UNIQUE_REPOSITORY_ID:
        file: FILE_TO_USE_TO_SAVE_THE_REPO_IN
        description: A_HUMAN_READABLE_STRING_DESCRIBING_THE_REPOSITORY
        baseurl: URL_TO_THE_DIRECTORY_WHERE_THE_YUM_REPOSITORYS_REPODATA_DIRECTORY_LIVES # not necessary
        mirrorlist: SPECIFIES_A_URL_TO_A_FILE_CONTAINING_A_LIST_OF_BASEURLS
        gpgkey: A_URL_POINTING_TO_THE_ASCII_ARMORED_GPG_KEY_FILE_FOR_THE_REPOSITORY
        enabled: yes
        gpgcheck: yes
        failovermethod: priority

Example 2 (only as a guideline, do not use it as epel is included in the pre-configured repositories):

    yum_repos_list_custom:
      epel:
        file: epel
        description: Extra Packages for Enterprise Linux 7 - $basearch
        baseurl: http://download.fedoraproject.org/pub/epel/7/$basearch
        mirrorlist: https://mirrors.fedoraproject.org/metalink?repo=epel-7&arch=$basearch
        gpgkey: file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
        enabled: yes
        gpgcheck: yes
        failovermethod: priority

## Dependencies

None

## License

MIT

## Author Information

Apostolos Tovletoglou [ansible-role-git](https://github.com/tovletoglou/ansible-role-yum-repos)
