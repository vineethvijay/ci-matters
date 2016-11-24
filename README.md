# ci-matters
Integration (comparison) of different continuous integration services on Android project.

### CI's integration

* [x] [Jenkins](https://github.com/vgaidarji/ci-matters/blob/master/JENKINS.md)
* [x] [Travis CI](https://github.com/vgaidarji/ci-matters/blob/master/TRAVIS.md) [![Build Status](https://travis-ci.org/vgaidarji/ci-matters.svg?branch=master)](https://travis-ci.org/vgaidarji/ci-matters)
* [x] [Bitrise](https://github.com/vgaidarji/ci-matters/blob/master/BITRISE.md) [![Build Status](https://www.bitrise.io/app/002b43ae8a42b6b1.svg?token=xT4EDBQWGNcSWJveU6IEVA&branch=master)](https://www.bitrise.io/app/002b43ae8a42b6b1)

### TODO

* [ ] TeamCity
* [ ] Buddybuild
* [ ] GreenHouse
* [ ] Gitlab CI
* [ ] Circle CI
* [ ] Drone.io
* [ ] Shippable
* [ ] Snap CI

---

# Comparison

This table should help people make a decision which CI to choose for the project.

| CI            | :dancers:,:construction_worker:,:mag_right::bug:,:vertical_traffic_light:,:mailbox_with_mail: | :iphone::eyes: | :shipit: | :page_facing_up: | :chart_with_upwards_trend: | :bust_in_silhouette:+:raised_hands:/:office:+:man: | :radio:/:computer: | :moneybag: |
| ------------- |:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Jenkins       |:star:|:star:|:star:|:star:|:star:|:bust_in_silhouette:+:raised_hands:|:radio:/:computer:|:free:|
| Travis        |.|.|.|.|.|.|.|.|
| Bitrise       |.|.|.|.|.|.|.|.|
| TeamCity      |.|.|.|.|.|.|.|.|
| Buddybuild    |.|.|.|.|.|.|.|.|
| Gitlab        |.|.|.|.|.|.|.|.|
| Circle        |.|.|.|.|.|.|.|.|
| Drone.io      |.|.|.|.|.|.|.|.|
| Shippable     |.|.|.|.|.|.|.|.|

1. :dancers: - clone 2. :construction_worker: - build 3. :mag_right::bug: - test 4. :vertical_traffic_light: - analyse 5. :mailbox_with_mail: - notify 
6. :iphone::eyes: - UI tests 7. :shipit: - [deploy](https://www.quora.com/GitHub-What-is-the-significance-of-the-Ship-It-squirrel) 8. :page_facing_up: - configuration file 9. :chart_with_upwards_trend: - visual reports
10. :bust_in_silhouette:+:raised_hands:/:office:+:man: - self-hosted/cloud 11. :radio:/:computer: - CI user interface (old/new) 12. :moneybag: - price
    

---

### Checkstyle

Project uses custom Checkstyle [rules](https://github.com/vgaidarji/ci-matters/blob/master/app/config/checkstyle/checkstyle-yopeso.xml).

---

### Fabric/Crashlytics project configuration

In order to upload APK to Crashlytics project should have following configuration:
`${projectDir}/fabric.properties` file with `apiSecret` and `io.fabric.ApiKey` in AndroidManifest.xml([1](https://github.com/vgaidarji/ci-matters/blob/master/app/src/main/AndroidManifest.xml#L17), 
[2](https://github.com/vgaidarji/ci-matters/blob/master/app/build.gradle#L59)) file.
**Both keys should not be uploaded to the repository for security reasons!**

Pass both parameters to your build from command line:

    ./gradlew -PfabricApiKey="YOUR_API_KEY" -PfabricApiSecret="YOUR_API_SECRET" crashlyticsUploadDistributionDebug
 
------

### Coveralls

[![Coverage Status](https://coveralls.io/repos/github/vgaidarji/ci-matters/badge.svg)](https://coveralls.io/github/vgaidarji/ci-matters)

`Coveralls` provides test coverage information. `COVERALLS_REPO_TOKEN` environment variable should be exported on the build machine.

