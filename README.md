[![Build Status](https://travis-ci.org/wireload/screenly-ose.svg?branch=master)](https://travis-ci.org/wireload/screenly-ose)
[![Coverage Status](https://coveralls.io/repos/wireload/screenly-ose/badge.svg?branch=master&service=github)](https://coveralls.io/github/wireload/screenly-ose?branch=master)

# Screenly OSE - Digital Signage for the Raspberry Pi

This is a fork of Screenly OSE with some very basic authentication added so the admin web interface is not wide open.

Instructions:
- Install from [this script](https://github.com/jpsingleton/screenly-ose/blob/master/misc/install.sh) (or just overwrite `server.py` with the file from this repo).
- Then [update the credentials manually](https://github.com/jpsingleton/screenly-ose/blob/master/server.py#L45) (defaults are `admin` and `Scr33nlyOSE`).
- It's also a _very_ good idea to enable SSL with [this script](https://github.com/jpsingleton/screenly-ose/blob/master/misc/enable_ssl.sh) (only HTTPS will work).

:shipit:

---

To learn more about Screenly, please visit the official website at [ScreenlyApp.com](http://www.screenlyapp.com). On the official site, you'll find the complete installation instructions, along with a live-demo of Screenly.

## Dockerized Development Environment

To simplify development of the server module of Screenly OSE, we've created a Docker container. This is intended to run on your local machine with the Screenly OSE repository mounted as a volume.

Assuming you're in the source code repository, simply run:

```
$ docker run --rm -ti \
  -p 8080:8080 \
  -v $(pwd):/home/pi/screenly \
  wireload/screenly-ose-server
```

## Disk Image Changelog

### 2015-02-25

 * Adds support for Raspberry Pi B+ V2.
 * Upgrades kernel and kernel modules.
 * Brings system packages up to date.
 * Various bug fixes.

### 2014-11-03

 * Adds a setting for time display in 24 or 12 hour formats.
 * System updates (including Bash and OpenSSL).
 * Solves a UTF8 bug ([#226](https://github.com/wireload/screenly-ose/issues/226)).
 * Various bug fixes.

### 2014-08-13

 * Adds support for Raspberry Pi Model B+.
 * Improves handling in `viewer.py` where the splash page is being displayed before `server.py` has been fully loaded.
 * Pulls in APT updates from Screenly's APT repository.
 * Other bug fixes up to commit 1946e252471fcf34c27903970fbde601189d65a5.

### 2014-07-17

 * Fixes issue with load screen failing to connect.
 * Adds support for video feeds ([#210](https://github.com/wireload/screenly-ose/issues/210)).
 * Resolves issue with assets not being added ([#209](https://github.com/wireload/screenly-ose/issues/209)).
 * Resolves issue with assets not moving to active properly ([#201](https://github.com/wireload/screenly-ose/issues/201)).
 * Pulls in APT updates from Screenly's APT repository.

### 2014-01-11

 * Upgrade kernel (3.10.25+) and firmware. Tracked in [this](https://github.com/wireload/rpi-firmware) fork.
 * Change and use Screenly's APT repository (apt.screenlyapp.com).
 * `apt-get upgrade` to the Screenly APT repository.
 * Update Screenly to latest version.
 * The disk image is available at [ScreenlyApp.com](http://www.screenlyapp.com).

## Running the Unit Tests

    nosetests --with-doctest

