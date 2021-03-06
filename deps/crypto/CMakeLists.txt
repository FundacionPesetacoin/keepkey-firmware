set(sources
    trezor-crypto/bip39.c
    trezor-crypto/hmac.c
    trezor-crypto/sha2.c
    trezor-crypto/base32.c
    trezor-crypto/hasher.c
    trezor-crypto/rand.c
    trezor-crypto/rc4.c
    trezor-crypto/blake256.c
    trezor-crypto/cash_addr.c
    trezor-crypto/curves.c
    trezor-crypto/rfc6979.c
    trezor-crypto/ed25519-donna/curve25519-donna-scalarmult-base.c
    trezor-crypto/ed25519-donna/ed25519-donna-32bit-tables.c
    trezor-crypto/ed25519-donna/ed25519.c
    trezor-crypto/ed25519-donna/curve25519-donna-helpers.c
    trezor-crypto/ed25519-donna/ed25519-keccak.c
    trezor-crypto/ed25519-donna/ed25519-sha3.c
    trezor-crypto/ed25519-donna/ed25519-donna-basepoint-table.c
    trezor-crypto/ed25519-donna/modm-donna-32bit.c
    trezor-crypto/ed25519-donna/curve25519-donna-32bit.c
    trezor-crypto/ed25519-donna/ed25519-donna-impl-base.c
    trezor-crypto/nem.c
    trezor-crypto/secp256k1.c
    trezor-crypto/bignum.c
    trezor-crypto/segwit_addr.c
    trezor-crypto/ripemd160.c
    trezor-crypto/groestl.c
    trezor-crypto/nist256p1.c
    trezor-crypto/memzero.c
    trezor-crypto/blake2b.c
    trezor-crypto/script.c
    trezor-crypto/bip32.c
    trezor-crypto/address.c
    trezor-crypto/blake2s.c
    trezor-crypto/sha3.c
    trezor-crypto/base58.c
    trezor-crypto/ecdsa.c
    trezor-crypto/pbkdf2.c
    trezor-crypto/aes/aeskey.c
    trezor-crypto/aes/aescrypt.c
    trezor-crypto/aes/aes_modes.c
    trezor-crypto/aes/aestab.c)

    # Clang 5.0 in the docker image (kktech/firmware:v7) is missing
    # <xmmintrin.h>, which breaks these. Until they're needed, we'll just elide
    # them.
    #trezor-crypto/chacha20poly1305/chacha_merged.c
    #trezor-crypto/chacha20poly1305/rfc7539.c
    #trezor-crypto/chacha20poly1305/poly1305-donna.c
    #trezor-crypto/chacha20poly1305/chacha20poly1305.c

include_directories(
  ${CMAKE_SOURCE_DIR}/deps/crypto/trezor-crypto
  ${OPENSSL_INCLUDE_DIR})

add_library(trezorcrypto ${sources})
