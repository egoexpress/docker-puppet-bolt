# Puppet Bolt Docker image

A Docker image for [Puppet Bolt](https://puppet.com/products/puppet-bolt), the task runner from Puppet which looks a lot like Ansible.

## Installation

    git clone https://github.com/egoexpress/docker-puppet-bolt.git
    cd docker-puppet-bolt
    docker build -t egoexpress/puppet-bolt .
    
# Usage

The container is configured to run `bolt` via CMD. The default argument is `--help`. 
Thus, if you just run the container with no supplied argument, you will see the help page.

    % docker run -it egoexpress/puppet-bolt:0.19
    Usage: bolt <subcommand> <action> [options]

    Available subcommands:
        bolt command run <command>       Run a command remotely
        bolt file upload <src> <dest>    Upload a local file
        bolt script run <script>         Upload a local script and run it remotely
        [..]

Supplied arguments to the Docker run will be handed to the bolt binary. So, to run `bolt task show`,
add the arguments to the `docker run` command:

    % docker run -it egoexpress/puppet-bolt:0.19 plan show
    aggregate::count
    aggregate::nodes
    canary
    facts
    facts::info
    facts::retrieve
    puppetdb_fact

    Use `bolt plan show <plan-name>` to view details and parameters for a specific plan.
