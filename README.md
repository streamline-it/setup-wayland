Role Name
=========

setup-wayland

This will setup the Wayland Graphical Environment

Requirements
------------

None

Role Variables
--------------

# defaults

# defaults file for setup-wayland

# user allowed to use the gui
setup_wayland_users:
  - username:

# name of the driver
setup_wayland_driver_name:
# package name for the driver
setup_wayland_pkg:

# driver directive in /etc/rc.conf
# Ex.
# setup_gui_environment_sysrc_directive:
#   - name: kld_list
#     value: "{{ setup_wayland_driver_name }}"

setup_wayland_sysrc_driver_directive:
  - name:
    value

# Vars section


FreeBSD vars file:

setup_wayland_pkgs:
  - wayland
  - seatd

setup_wayland_services:
  - seatd

setup_wayland_sysrc_arguments:
  - service: seatd_enable
    value: "YES"

Dependencies
------------
None

Example Playbook
----------------

- name: setup wayland
  hosts: node4.example.com
  become: true

  vars:

    # defaults file for setup-gui-environment

    setup_wayland_driver_name: i915kms
    setup_wayland_driver_pkg: drm-kmod

    setup_wayland_sysrc_driver_directive:
      - name: kld_list
        value: "{{ setup_wayland_driver_name }}"

    # user allowed to user the gui
    setup_wayland_users:
      - username: rich

  roles:

    - name: setup-wayland

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
