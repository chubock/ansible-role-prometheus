Role Name
=========

A role to install `Prometheus`.

Role Variables
--------------

specify all your jobs with `jobs` variable. each job's key is the job name which must have a `targets` property which specifies the endpoints to collect metrics from. it also can have a `scrape_interval` to override `global.scrape_interval` for that job. following variables are defined at default/main.yml:

Path to install Prometheus

    prometheus_path: /var/lib/prometheus
    
URL to download Prometheus binaries

    prometheus_url: "https://github.com/prometheus/prometheus/releases/download/v2.23.0/prometheus-2.23.0.linux-amd64.tar.gz"
    
path to prometheus configuration template file. 

    prometheus_config_template: prometheus.yml.j2
    
path to prometheus systemd service template file.

    prometheus_service_template: prometheus.service.j2
    
global scrape_interval in prometheus configuration file.

    global_scrape_interval: 10s

global evaluation_interval in prometheus configuration file.

    global_evaluation_interval: 10s
    
Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
    
    - hosts: servers
      become: yes
      roles:
        - { role: chubock.prometheus}
      vars:
        jobs:
          mongo:
            targets:
              - mongodb1.local:9001
              - mongodb2.local:9001
          elasticsearch:
            targets:
              - es1.local:9114
              - es2.local:9114
              - es3.local:9114
            scrape_interval: 30s

License
-------

Apache-2

Author Information
------------------

you can contact me via my email: chubock@gmail.com and my linkedin account: https://www.linkedin.com/in/chubock/
