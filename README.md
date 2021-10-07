Docker-Plex
=========

A role to spin up a Plex docker container. This is only being published for integration into my AWX instance. 

Requirements
------------

Docker needs to be installed and configured on the server. 

Role Variables
--------------

Required variables are listed here, along with default example values. Any of these defaults can be overwritten by using the vars role directory. 

    plex_name: plex

This is the name of the container. 

    plex_image: linuxserver/plex

The image container. By default this pulls from linuxserver.io.

    plex_ports:
     - 7878:7878
     - 8787:8787

These are the exported ports of the container.

    plex_config_directory: /opt/plex

This is the directory that config files will be stored. This is mapped to /config in the container. 

    plex_movie_directory: /mnt/media/movies

This is the directory that Plex will move movies and managed files to. Usually we want this directory on some sort of media network storage. This is mapped to /movies inside the container.

    plex_movie_directory: /mnt/media/movies

This is where files will be placed for Plex to manage, either via a download client or manually. This is mapped to /completed inside the container.

    plex_environment_variables:
      PUID: "1000"
      PGID: "1000"
      TZ: America/Chicago

This is a dictionary of extra environment variables for the container. 

    plex_docker_additional_options:
      restart_policy: unless-stopped

Another dictionary, this time of additional options for the container. By default, this sets the container to start on boot unless it was previously stopped. 

    plex_config:
      ApiKey: "abc123"
      UrlBase: "example.com"
      LaunchBrowser: "False"
      AnalyticsEnabled: "False"

This is not currently in use - the applicable code is commented out in the task. 

Dependencies
------------

None.

Example Playbook
----------------

    - name: Deploy the Plex Container.
      hosts: rr
      become: true
      roles:
      - role: docker-plex

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/