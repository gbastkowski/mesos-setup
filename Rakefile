require 'marathon'

Marathon.url = 'http://marathon.docker.localhost'

namespace :www do
  task :deploy do
    Marathon::App.start(
      id:        '/www',
      instances: 1,
      cpus:      0.2,
      mem:       128,
      container: {
        type: :DOCKER,
        docker: {
          image:          'nginx:stable-alpine',
          forcePullImage: true,
          privileged:     false,
          parameters:     [
            { key: :rm, value: 'true' }
          ]
        }
      },
    )
  end

  task :undeploy do
    Marathon::App.delete '/www'
  end
end
