# @zap/logging

Shared structured-logging library for zap Node services, built on pino. See
[../compliance/policy/logging-libraries.md](../compliance/policy/logging-libraries.md) for
the full behavior contract (L-1...L-13).

This is the Node package for zap's logging policy. The Python equivalent (`zap_logging`) lives
in the separate [`zap-logging-py`](https://github.com/Zapata-Group/zap-logging-py) repo — the two
were split out of a shared mono-repo because npm has no native subdirectory-pin support for git
dependencies (only pip does), so a single repo couldn't serve both `github:` install forms.

## Install

```
npm install github:Zapata-Group/zap-logging-node#v1.0.0
```

package.json lives at the repo root, so plain `github:` installs resolve without any subdirectory
pin.

## Usage

```js
const { logger, audit, registerAuditSink } = require('@zap/logging');

logger.info({ event: 'mail.send', outcome: 'success', request_id, to_count }, 'sent');
logger.error({ event: 'mail.send', outcome: 'failure', error_code }, 'send failed');

audit('mail.send', { outcome: 'success', user, source_ip, target });
```
