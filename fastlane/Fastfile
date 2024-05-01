default_platform(:android)

platform :android do
  desc "Submit a new Internal Build to Play Store internal track"
  lane :internal do
    # Your lane logic here
    # For example:
    # sh "gradle assembleRelease"

    # Assuming you have a Gradle-based project, you might want to use something like:
    gradle(
      task: "assembleRelease",
      properties: {
        "android.injected.signing.store.file" => "path/to/your/keystore",
        "android.injected.signing.store.password" => ENV["KEYSTORE_PASSWORD"],
        "android.injected.signing.key.alias" => "your-alias",
        "android.injected.signing.key.password" => ENV["KEY_PASSWORD"]
      }
    )

    upload_to_play_store(
      track: "internal",
      aab: "app/build/outputs/bundle/release/app-release.aab",
      skip_upload_images: true,
      skip_upload_screenshots: true
    )
  end
end
