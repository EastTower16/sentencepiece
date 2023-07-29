package(default_visibility = ["//visibility:public"])

proto_library(
    name = "sentencepiece_model_proto",
    srcs = [
        "sentencepiece_model.proto",
    ],
)

cc_proto_library(
    name = "sentencepiece_model_cc_proto",
    deps = [":sentencepiece_model_proto"],
    
)

proto_library(
    name = "sentencepiece_proto",
    srcs = [
        "sentencepiece.proto",
    ],
)

cc_proto_library(
    name = "sentencepiece_cc_proto",
    deps = [":sentencepiece_proto"],
)


cc_library(
    name = "common",
    srcs = ["common.h","config.h"],
    deps=[
        
    ],
    includes=["src"],
)

# https://docs.bazel.build/versions/master/be/c-cpp.html#cc_library
cc_library(
    name = "sentencepiece_processor",
    srcs = ["sentencepiece_processor.cc"],
    hdrs = ["sentencepiece_processor.h"],
    deps = [
        ":common",
        ":error",
        ":filesystem",
        ":model_factory",
        ":sentencepiece_cc_proto",
        ":normalizer",
        "@com_google_absl//absl/strings",
    ],
    includes=["src"],
)

cc_library(
    name = "util",
    srcs = [
        "util.cc",
        "util.h",
        "sentencepiece_processor.h",
    ],
    deps = [
        ":common",
        # ":sentencepiece_processor",
        "@com_google_absl//absl/strings",
    ],
    includes=["src"],
)

cc_library(
    name = "error",
    srcs = [
        "error.cc",
        "init.h",
    ],
    deps = [
        ":util",
        "@com_google_absl//absl/flags:flag",
        "@com_google_absl//absl/flags:parse",
        "@com_google_protobuf//:protobuf_headers",
    ],
    includes=["src"],
)



cc_library(
    name = "model_interface",
    srcs = [
        "model_interface.cc",
        "model_interface.h",
    ],
    deps = [
        ":sentencepiece_model_cc_proto",
        ":util",
        "@com_google_absl//absl/strings",
        "@com_google_absl//absl/container:flat_hash_map",
        "//third_party/darts_clone:darts",
    ],
    includes=["src"],
)

cc_library(
    name = "bpe_model",
    srcs = [
        "bpe_model.cc",
        "bpe_model.h",
    ],
    deps = [
        ":model_interface",
    ],
    includes=["src"],
)

cc_library(
    name = "char_model",
    srcs = [
        "char_model.cc",
        "char_model.h",
    ],
    deps = [
        ":model_interface",
    ],
    includes=["src"],
)

cc_library(
    name = "unigram_model",
    srcs = [
        "unigram_model.cc",
        "unigram_model.h",
    ],
    deps = [
        ":model_interface",
    ],
    includes=["src"],
)

cc_library(
    name = "word_model",
    srcs = [
        "word_model.cc",
        "word_model.h",
    ],
    deps = [
        ":model_interface",
    ],
    includes=["src"],
)

# https://docs.bazel.build/versions/master/be/c-cpp.html#cc_library
cc_library(
    name = "model_factory",
    srcs = [
        "model_factory.cc",
        "model_factory.h",
    ],
    deps = [
        ":bpe_model",
        ":char_model",
        ":unigram_model",
        ":word_model",
    ],
    includes=["src"],
)

cc_library(
    name = "normalizer",
    srcs = [
        "normalizer.cc",
        "normalizer.h",
    ],
    deps = [
        ":sentencepiece_model_cc_proto",
        ":sentencepiece_cc_proto",
        ":util",
        "//third_party/darts_clone:darts",
    ],
    includes=["src"],
)


cc_library(
    name = "builder",
    srcs = [
        "builder.cc",
        "builder.h",
        "normalization_rule.h",
    ],
    deps = [
        ":sentencepiece_model_cc_proto",
        ":util",
        ":error",
        ":normalizer",
        "@com_google_absl//absl/strings",
        "//third_party/darts_clone:darts",
    ],
    includes=["src"],
)

cc_library(
    name = "unicode_script",
    srcs = [
        "unicode_script.cc",
        "unicode_script.h",
        "unicode_script_map.h",
    ],
    deps = [
        ":util",
         "@com_google_absl//absl/container:flat_hash_map"
    ],
    includes=["src"],
)

cc_library(
    name = "trainer_interface",
    srcs = [
        "trainer_interface.cc",
        "trainer_interface.h",
    ],
    deps = [
        ":util",
        ":error",
        ":unicode_script",
        ":model_factory",
        ":normalizer",
        "@com_google_absl//absl/container:flat_hash_set",
        "@com_google_absl//absl/random",
    ],
    includes=["src"],
)


cc_library(
    name = "bpe_model_trainer",
    srcs = [
        "bpe_model_trainer.cc",
        "bpe_model_trainer.h",
    ],
    deps = [
        ":trainer_interface",
    ],
    includes=["src"],
)

cc_library(
    name = "char_model_trainer",
    srcs = [
        "char_model_trainer.cc",
        "char_model_trainer.h",
    ],
    deps = [
        ":trainer_interface",
    ],
    includes=["src"],
)

cc_library(
    name = "unigram_model_trainer",
    srcs = [
        "unigram_model_trainer.cc",
        "unigram_model_trainer.h",
    ],
    deps = [
        ":trainer_interface",
        "//third_party/esaxx:esaxx",
    ],
    includes=["src"],
)

cc_library(
    name = "word_model_trainer",
    srcs = [
        "word_model_trainer.cc",
        "word_model_trainer.h",
    ],
    deps = [
        ":trainer_interface",
    ],
    includes=["src"],
)


cc_library(
    name = "trainer_factory",
    srcs = [
        "trainer_factory.cc",
        "trainer_factory.h",
    ],
    deps = [
        ":bpe_model_trainer",
        ":char_model_trainer",
        ":unigram_model_trainer",
        ":word_model_trainer",
    ],
    includes=["src"],
)

cc_library(
    name="filesystem",
    srcs=[
        "filesystem.cc",
        "filesystem.h",
    ],
    deps=[
        ":util",
    ],
    includes=["src"],
)

cc_library(
    name = "pretokenizer_for_training",
    srcs = [
        "pretokenizer_for_training.cc",
        "pretokenizer_for_training.h",
    ],
    deps = [
        ":util",
        ":sentencepiece_processor",
        ":sentencepiece_cc_proto",
    ],
    includes=["src"],
)

cc_library(
    name = "sentencepiece_trainer",
    srcs = [
        "sentencepiece_trainer.cc",
        "sentencepiece_trainer.h",
    ],
    deps = [
        ":trainer_factory",
        ":normalizer",
        ":builder",
        ":filesystem",
        ":sentencepiece_processor",
        ":sentencepiece_cc_proto",
        ":pretokenizer_for_training",
    ],
    includes=["src"],
)

cc_binary(
    name = "spm_train",
    srcs = [
        "spm_train_main.cc",
    ],
    deps = [
        ":sentencepiece_trainer",
        ":error",
        
    ],
)

cc_binary(
    name = "spm_decode",
    srcs = [
        "spm_decode_main.cc",
    ],
    deps = [
        ":model_factory",
        ":sentencepiece_processor",
        ":error",
    ],
)

cc_binary(
    name = "spm_encode",
    srcs = [
        "spm_encode_main.cc",
    ],
    deps = [
        ":model_factory",
        ":sentencepiece_trainer",
        ":sentencepiece_processor",
        ":error",
    ],
)


cc_binary(
    name = "spm_normalize",
    srcs = [
        "spm_normalize_main.cc",
    ],
    deps = [
        ":model_factory",
        ":sentencepiece_trainer",
        ":sentencepiece_processor",
        ":error",
    ],
)