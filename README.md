# UBITQUITY-GeoServer-Security-Patch
An emergency security patch by UBITQUITY to mitigate the unauthenticated SQL injection zero-day vulnerability in GeoServer's jsonArrayContains function. This hotfix sanitizes input parameters for PostGIS and Oracle DataStores to prevent potential Remote Code Execution (RCE).
