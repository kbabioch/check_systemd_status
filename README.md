# check_systemd_status

This is a script that will check the systemd(1) status by parsing the output
of systemctl(1). It will signal warning (1) and/or critical (2) conditions
via the exit code when the system - as perceived by systemd - it not (yet)
in optimal (i.e. running) state.

This can, for instance, be used as a simple Nagios / Icinga check in order to
monitor the overall system status.

## USAGE

This script can be invoked without any additional arguments. It will, in return
invoke `systemctl` and parse its output. The `--systemctl-path` argument can
be used to specify a location to the `systemctl` binary explicitly, in case
it is not within `$PATH`.

## EXIT CODES

This plugin will exit with codes that are compliant with the typical Nagios /
Icinga (2) [convention][icinga-exit-codes]. More specifically it will indicate
a `warning` state when there are queued jobs and a `critical` state when there
are failed units. In case of failure (i.e. `systemctl` not being available), it
will indicate an `unknown` situation. Otherwise `ok` is being returned.

## LICENSE

[![GNU GPLv3](http://www.gnu.org/graphics/gplv3-127x51.png "GNU GPLv3")](http://www.gnu.org/licenses/gpl.html)

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

[icinga-exit-codes]: https://icinga.com/docs/icinga2/latest/doc/03-monitoring-basics/#service-states
