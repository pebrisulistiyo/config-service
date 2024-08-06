# Build
custom_build(
    # Name of the container image
    ref = 'config-service',
    # Command to build the container image
    command = './mvnw spring-boot:build-image -DskipTests -Dspring-boot.build-image.imageName=$EXPECTED_REF',
    # Files to watch that trigger a new build
    deps = ['pom.xml', 'src']
)

# Deploy
k8s_yaml(['k8s/deployment.yaml', 'k8s/service.yaml'])

# Manage
k8s_resource('config-service', port_forwards=['9001'])