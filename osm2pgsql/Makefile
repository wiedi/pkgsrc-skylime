# $NetBSD$

DISTNAME=	0.84.0
PKGNAME=	osm2pgsql-${DISTNAME}
CATEGORIES=	geography
MASTER_SITES=	https://github.com/openstreetmap/osm2pgsql/archive/

MAINTAINER=	wiedi@frubar.net
HOMEPAGE=	https://github.com/openstreetmap/osm2pgsql/
COMMENT=	OpenStreetMap data to PostgreSQL converter
LICENSE=	gnu-gpl-v2

WRKSRC=		${WRKDIR}/osm2pgsql-0.84.0
USE_LANGUAGES=	c99 c++
USE_LIBTOOL=	yes
USE_TOOLS+=	gmake autoconf aclocal automake
GNU_CONFIGURE=	yes

CONFIGURE_ARGS+=	--with-zlib=${BUILDLINK_PREFIX.zlib}
CONFIGURE_ARGS+=	--with-bzip2=${BUILDLINK_PREFIX.bzip2}
CONFIGURE_ARGS+=	--with-proj=${BUILDLINK_PREFIX.proj}

.include "../../mk/bsd.prefs.mk"

# 'grep -o' require GNU grep
.if ${OPSYS} == "SunOS"
BUILD_DEPENDS+=		grep-[0-9]*:../../textproc/grep
TOOLS_PATH.grep=	${LOCALBASE}/bin/ggrep
.endif

pre-configure:
	cd ${WRKSRC} && aclocal && ./autogen.sh

.include "../../textproc/libxml2/buildlink3.mk"
.include "../../geography/geos/buildlink3.mk"
.include "../../geography/proj/buildlink3.mk"
.include "../../archivers/bzip2/buildlink3.mk"
.include "../../devel/zlib/buildlink3.mk"
.include "../../databases/postgresql-postgis/buildlink3.mk"
.include "../../lang/lua/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
