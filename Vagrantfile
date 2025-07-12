# -*- mode: ruby -*-
# vi: set ft=ruby :

# ENV['VAGRANT_NO_PARALLEL'] = 'yes'
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'


Vagrant.configure("2") do |config|
    boxes = [
        { "name": "lb-1", "box": "generic/ubuntu2204", "version": "4.2.16", "memory": 1024, "cpu": 2 },
        { "name": "apps-1", "box": "generic/ubuntu2204", "version": "4.2.16", "memory": 1024, "cpu": 2 },
        # { "name": "data-1", "box": "generic/ubuntu2204", "version": "4.2.16", "memory": 4024, "cpu": 4 },
        # { "name": "gitlab-1", "box": "generic/ubuntu2204", "version": "4.2.16", "memory": 4024, "cpu": 4 },
        # { "name": "minio-1", "box": "generic/ubuntu2204", "version": "4.2.16", "memory": 4024, "cpu": 4 },
        # { "name": "monitor-1", "box": "generic/ubuntu2204", "version": "4.2.16", "memory": 4024, "cpu": 4 },
        # { "name": "windows2022-1", "box": "peru/windows-server-2022-standard-x64-eval", "version": "20231201.01", "memory": 8192, "cpu": 4 },
        # { "name": "windows2022-2", "box": "peru/windows-server-2022-standard-x64-eval", "version": "20231201.01", "memory": 8192, "cpu": 4 },
        # { "name": "windows2022-3", "box": "peru/windows-server-2022-standard-x64-eval", "version": "20231201.01", "memory": 8192, "cpu": 4 },
        # { "name": "windows2022-4", "box": "peru/windows-server-2022-standard-x64-eval", "version": "20231201.01", "memory": 8192, "cpu": 4 },
    ]

    boxes.each_with_index do |opts, index|
        config.vm.define opts[:name] do |box|
            box.vm.box              = "#{opts[:box]}"
            box.vm.box_check_update = false
            box.vm.box_version      = "#{opts[:version]}"
            box.vm.network "private_network", ip: "10.0.0.1#{index}"

            if opts[:name].start_with?('windows')
                box.vm.hostname  = "#{opts[:name]}issa"
            else
                box.vm.hostname  = "#{opts[:name]}.is.sa"
            end

            box.vm.provider :virtualbox do |v|
                v.name   = "#{opts[:name]}.is.sa"
                v.memory = opts[:memory]
                v.cpus   = opts[:cpu]
            end

            box.vm.provider :libvirt do |v|
                v.memory  = opts[:memory]
                v.cpus    = opts[:cpu]
                v.suspend_mode="managedsave"
            end
        end
    end
end