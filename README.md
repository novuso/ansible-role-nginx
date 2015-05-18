# Ansible Role: Nginx

[![Ansible Galaxy](http://img.shields.io/badge/galaxy-novuso.nginx-000000.svg)](https://galaxy.ansible.com/list#/roles/3818)
[![MIT License](http://img.shields.io/badge/license-MIT-003399.svg)](http://opensource.org/licenses/MIT)

An Ansible role that manages Nginx on Ubuntu 14.04

## Requirements

None

## Role Variables

**TODO**

## Dependencies

None

## Example Playbook

    ---
    - hosts: all
      vars:
      - nginx_server_configs:
        - name: "project"
          servers:
          - listen: ["80 default_server"]
            server_name: "project.dev"
            root: "/var/www/html"
            index: "index.html index.htm"
            charset: "utf-8"
            access_log: "/var/log/nginx/project.log"
            error_log: "/var/log/nginx/project-error.log error"
            includes: ["h5bp/basic.conf"]
            locations:
            - match: "= /favicon.ico"
              access_log: "off"
              log_not_found: "off"
            - match: "= /robots.txt"
              access_log: "off"
              log_not_found: "off"
            - match: "/"
              try_files: "$uri $uri/ =404"
      roles:
      - novuso.nginx

## License

This is released under the [MIT license](http://opensource.org/licenses/MIT).
