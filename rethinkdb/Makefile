# $NetBSD$

VERSION=	1.11.3
DISTNAME=	v${VERSION}
PKGNAME=	rethinkdb-${VERSION}
CATEGORIES=	databases
MASTER_SITES=	https://github.com/rethinkdb/rethinkdb/archive/

MAINTAINER=	wiedi@frubar.net
HOMEPAGE=	http://rethinkdb.com/
COMMENT=	Distributed JSON document database with a powerful query language
LICENSE=	gnu-agpl-v3

WRKSRC=		${WRKDIR}/rethinkdb-1.11.3
HAS_CONFIGURE=	yes
USE_LANGUAGES=	c c++
USE_TOOLS+=	gmake
CONFIGURE_ARGS+=	--without-tcmalloc

CFLAGS+= -DDISABLE_BREAKPOINTS

.include "../../mk/bsd.prefs.mk"

.if ${OPSYS} == "SunOS"
BUILD_DEPENDS+=		grep-[0-9]*:../../textproc/grep
TOOLS_PATH.grep=	${LOCALBASE}/bin/ggrep
TOOLS_PATH.egrep=	${LOCALBASE}/bin/gegrep
.endif

.include "../../devel/protobuf/buildlink3.mk"
.include "../../wip/v8-316/buildlink3.mk"
.include "../../devel/boost-headers/buildlink3.mk"
.include "../../devel/boost-libs/buildlink3.mk"

.include "../../mk/bsd.pkg.mk"
