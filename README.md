# SIM_A7670C_ESP
change the following line in ssl_client.cpp ->
  #ifndef MBEDTLS_KEY_EXCHANGE__SOME__PSK_ENABLED
  #error "Please configure IDF framework to include mbedTLS -> Enable pre-shared-key ciphersuites and activate at least one cipher"
  #endif
To ->
  #if !defined(MBEDTLS_KEY_EXCHANGE__SOME__PSK_ENABLED) && !defined(MBEDTLS_KEY_EXCHANGE_SOME_PSK_ENABLED)
  #warning "Please configure IDF framework to include mbedTLS -> Enable pre-shared-key ciphersuites and activate at least one cipher"
  #endif

Add the following to the sdkcongig file
  #
  # TLS Key Exchange Methods
  #
  CONFIG_MBEDTLS_PSK_MODES=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_PSK=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDHE_PSK=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_RSA_PSK=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_RSA=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_ELLIPTIC_CURVE=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDHE_RSA=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDHE_ECDSA=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDH_ECDSA=y
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDH_RSA=y
  # end of TLS Key Exchange Methods
