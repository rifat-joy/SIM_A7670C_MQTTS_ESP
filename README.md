# SIM_A7670C_ESP

## change the following line in ssl_client.cpp ->

  #ifndef MBEDTLS_KEY_EXCHANGE__SOME__PSK_ENABLED <br />
  #error "Please configure IDF framework to include mbedTLS -> Enable pre-shared-key ciphersuites and activate at least one cipher" <br />
  #endif <br />
  
## To ->

  #if !defined(MBEDTLS_KEY_EXCHANGE__SOME__PSK_ENABLED) && !defined(MBEDTLS_KEY_EXCHANGE_SOME_PSK_ENABLED) <br />
  #warning "Please configure IDF framework to include mbedTLS -> Enable pre-shared-key ciphersuites and activate at least one cipher" <br />
  #endif <br />

## Add the following to the sdkcongig file
  
  #TLS Key Exchange Methods <br />
  
  CONFIG_MBEDTLS_PSK_MODES=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_PSK=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDHE_PSK=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_RSA_PSK=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_RSA=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_ELLIPTIC_CURVE=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDHE_RSA=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDHE_ECDSA=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDH_ECDSA=y <br />
  CONFIG_MBEDTLS_KEY_EXCHANGE_ECDH_RSA=y <br />
  #end of TLS Key Exchange Methods
