# Copyright 2009 Google Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

vars = {
  # chromium.org and googlecode.com will redirect https URLs for directories
  # that don't end with a trailing slash to http. We therefore try to make sure
  # all https URLs include the trailing slash, but it's unclear if SVN actually
  # respects this.
  "chromium_trunk": "https://src.chromium.org/svn/trunk/",
  # We don't include @ inside the revision here as is customary since
  # we want to pass this into a -D flag
  "chromium_revision_num": "256281",
  "chromium_deps_root": "src/third_party/chromium_deps",

  "libpagespeed_svn_root": "https://page-speed.googlecode.com/svn/",
  "libpagespeed_trunk": "https://page-speed.googlecode.com/svn/lib/trunk/",
  "libpagespeed_revision": "@2439",

  # Import libwebp 0.4.1 from the official repo.
  "libwebp_src": "https://chromium.googlesource.com/webm/libwebp.git",
  "libwebp_revision": "@8af2771813632e2007988c8df6ad7e68b28ad121",

  "modspdy_src": "https://mod-spdy.googlecode.com/svn/trunk/src/",
  "modspdy_revision": "@387",

  "serf_src": "https://serf.googlecode.com/svn/tags/1.1.0/",
  "serf_revision": "@head",

  "apr_src": "https://svn.apache.org/repos/asf/apr/apr/tags/1.4.2/",
  "apr_revision": "@head",

  "aprutil_src": "https://svn.apache.org/repos/asf/apr/apr-util/tags/1.3.9/",
  "aprutil_revision": "@head",

  "apache_httpd_src":
    "https://svn.apache.org/repos/asf/httpd/httpd/tags/2.2.15/",
  "apache_httpd_revision": "@head",

  # TODO(morlovich) We can't actually run with 2.4.1; but 2.4.2 isn't tagged yet
  # and the headers are certainly good enough.
  "apache_httpd24_src":
    "https://svn.apache.org/repos/asf/httpd/httpd/tags/2.4.1/",
  "apache_httpd24_revision": "@head",

  "jsoncpp_src": "https://github.com/open-source-parsers/jsoncpp.git",
  "jsoncpp_revision": "@7165f6ac4c482e68475c9e1dac086f9e12fff0d0",

  "gflags_root":
    "https://gflags.googlecode.com/svn/tags/gflags-1.5/src/",
  "gflags_revision": "@head",

  "google_sparsehash_root":
    "https://sparsehash.googlecode.com/svn/tags/sparsehash-1.8.1/src/",
  "google_sparsehash_revision": "@head",

  "gtest_src": "https://googletest.googlecode.com/svn/tags/release-1.7.0/",
  "gtest_revision": "@head",

  "gmock_src": "https://googlemock.googlecode.com/svn/tags/release-1.7.0/",
  "gmock_revision": "@head",

  # Comment this out to disable HTTPS fetching via serf.  See also the
  # references in src/third_party/serf/serf.gyp.
  #
  # TODO(jmarantz): create an easy way to choose this option from the
  # 'gclient' command, without having to edit the gyp & DEPS files.
  #
  # BoringSSL commit picked on Dec 4, 2015
  # https://chromium.googlesource.com/chromium/src.git/+/10f4f96db4f6e67316f5e5b6aa92b73947509ac5
  "boringssl_src": "https://boringssl.googlesource.com/boringssl.git",
  "boringssl_git_revision": "@6d9e5a74482bb832a6b4d9ae3d20d8f10f250bbd",

  "domain_registry_provider_src":
     "https://domain-registry-provider.googlecode.com/svn/trunk/",
  "domain_registry_provider_revision": "@31",
}

deps = {

  # Fetch dependent DEPS so we can sync our other dependencies relative
  # to them.
  Var("chromium_deps_root"):
    File(Var("chromium_trunk") + "src/DEPS@" + Var("chromium_revision_num")),

  # Other dependencies.
  "src/build/temp_gyp":
    Var("libpagespeed_trunk") + "src/build/temp_gyp/" +
        Var("libpagespeed_revision"),

  # We check 'build/android' out of Chromium repo to get
  # 'android/cpufeatures.gypi', which is needed to compile libwebp.
  "src/build/android":
    Var("chromium_trunk") + "src/build/android/@" +
        Var("chromium_revision_num"),
  "src/build/ios":
    Var("chromium_trunk") + "src/build/ios/@" + Var("chromium_revision_num"),
  "src/build/internal":
    Var("chromium_trunk") + "src/build/internal/@" +
        Var("chromium_revision_num"),
  "src/build/linux":
    Var("chromium_trunk") + "src/build/linux/@" + Var("chromium_revision_num"),
  "src/build/mac":
    Var("chromium_trunk") + "src/build/mac/@" + Var("chromium_revision_num"),
  "src/build/win":
    Var("chromium_trunk") + "src/build/win/@" + Var("chromium_revision_num"),

  # TODO(huibao): Remove references to libpagespeed.
  "src/third_party/giflib":
    Var("libpagespeed_svn_root") + "deps/giflib-4.1.6/",
  "src/third_party/icu": Var("libpagespeed_svn_root") + "deps/icu461/",
  "src/third_party/optipng":
    Var("libpagespeed_svn_root") + "deps/optipng-0.7.4/",
  "src/third_party/zlib": Var("libpagespeed_svn_root") + "deps/zlib-1.2.5/",

  # Yasm assember is required for libjpeg_turbo.
  "src/third_party/libjpeg_turbo/yasm":
    Var("chromium_trunk") + "src/third_party/yasm/@" +
        Var("chromium_revision_num"),

  "src/third_party/libjpeg_turbo/yasm/source/patched-yasm":
    Var("chromium_trunk") + "deps/third_party/yasm/patched-yasm/@" +
        Var("chromium_revision_num"),

  "src/third_party/libjpeg_turbo/src":
    Var("chromium_trunk") + "deps/third_party/libjpeg_turbo/@" +
        Var("chromium_revision_num"),

  "src/testing":
    Var("chromium_trunk") + "src/testing/@" + Var("chromium_revision_num"),
  "src/testing/gtest": Var("gtest_src") + Var("gtest_revision"),
  "src/testing/gmock": Var("gmock_src") + Var("gmock_revision"),


  "src/third_party/apr/src":
    Var("apr_src") + Var("apr_revision"),

  "src/third_party/aprutil/src":
    Var("aprutil_src") + Var("aprutil_revision"),

  "src/third_party/httpd/src/include":
    Var("apache_httpd_src") + "include/" + Var("apache_httpd_revision"),

  "src/third_party/httpd/src/os":
    Var("apache_httpd_src") + "os/" + Var("apache_httpd_revision"),

  "src/third_party/httpd24/src/include":
    Var("apache_httpd24_src") + "include/" + Var("apache_httpd24_revision"),

  "src/third_party/httpd24/src/os":
    Var("apache_httpd24_src") + "os/" + Var("apache_httpd24_revision"),

  "src/third_party/chromium/src/base":
    Var("chromium_trunk") + "src/base/@" + Var("chromium_revision_num"),

  "src/third_party/chromium/src/build":
    Var("chromium_trunk") + "src/build/@" + Var("chromium_revision_num"),

  "src/third_party/chromium/src/net/base":
     Var("chromium_trunk") + "src/net/base@" + Var("chromium_revision_num"),

  "src/third_party/chromium/src/url":
    Var("chromium_trunk") + "src/url@" + Var("chromium_revision_num"),

  "src/third_party/gflags/src": Var("gflags_root") + Var("gflags_revision"),
  "src/third_party/google-sparsehash/src":
    Var("google_sparsehash_root") + Var("google_sparsehash_revision"),

  "src/third_party/protobuf":
    Var("chromium_trunk") + "src/third_party/protobuf/@" +
        Var("chromium_revision_num"),

  # Json cpp.
  "src/third_party/jsoncpp/src":
    Var("jsoncpp_src") + Var("jsoncpp_revision"),

  # Serf
  "src/third_party/serf/src": Var("serf_src") + Var("serf_revision"),

  "src/third_party/mod_spdy/src": Var("modspdy_src") + Var("modspdy_revision"),

  "src/third_party/libwebp": Var("libwebp_src") + Var("libwebp_revision"),

  "src/tools/clang":
    Var("chromium_trunk") + "src/tools/clang/@" + Var("chromium_revision_num"),

  "src/tools/gyp": From(Var("chromium_deps_root")),

  "src/third_party/modp_b64":
    Var("chromium_trunk") + "src/third_party/modp_b64/@" +
        Var("chromium_revision_num"),

  # RE2.
  "src/third_party/re2/src":
    Var("chromium_trunk") + "src/third_party/re2/@" +
        Var("chromium_revision_num"),

  # Comment to disable HTTPS fetching via serf.  See also the
  # references in src/third_party/serf/serf.gyp.
  #
  "src/third_party/boringssl/src":
    Var("boringssl_src") + Var("boringssl_git_revision"),

  # Domain Registry Provider gives us the Public Suffix List.
  "src/third_party/domain_registry_provider":
    Var("domain_registry_provider_src") +
        Var("domain_registry_provider_revision")
}


deps_os = {
  "win": {
    "src/third_party/cygwin": From(Var("chromium_deps_root")),
    "src/third_party/python_26":
      Var("chromium_trunk") + "tools/third_party/python_26/@" +
          Var("chromium_revision_num"),
  },
  "mac": {
  },
  "unix": {
  },
}


include_rules = [
  # Everybody can use some things.
  "+base",
  "+build",
]


# checkdeps.py shouldn't check include paths for files in these dirs:
skip_child_includes = [
   "testing",
]


hooks = [
   {
    # Pull clang on mac. If nothing changed, or on non-mac platforms, this takes
    # zero seconds to run. If something changed, it downloads a prebuilt clang,
    # which takes ~20s, but clang speeds up builds by more than 20s.
    "pattern": ".",
    "action": ["python", "src/tools/clang/scripts/update.py", "--mac-only"],
  },
  {
    # A change to a .gyp, .gypi, or to GYP itself should run the generator.
    "pattern": ".",
    "action": ["python", "src/build/gyp_chromium",
               "-Dchromium_revision=" + Var("chromium_revision_num")],
  },
]
