# Making Code Changes to the Gem Theme

Publishing changes to the gem theme requires multiple steps:
1. Commit code changes to `git`
2. Bump appropriate version number in `kcc-gem-theme.gemspec` (following SemVer 2.0.0 standards) & commit to `git`
3. Push commits to GitHub
4. Build the Gem
5. Push the Gem to RubyGems.org

Using the new version in a project has some requirements as well:
1. Update the Gem on your machine
2. Update the project's Gem
3. Push a change to GitHub to force a rebuild with the new version

## Developing in the Gem Theme

### `kcc-gem-theme.gemspec`

The `kcc-gem-theme.gemspec` file defines the parameters for the RubyGems project:
```ruby
# frozen_string_literal: true

Gem::Specification.new do |spec|
  spec.name          = "kcc-gem-theme"
  spec.version       = "1.22.5"
  spec.authors       = ["<RUBYGEMS_USER>"]
  spec.email         = ["<RUBYGEMS_EMAIL>"]

  spec.summary       = "KCC's Gem-based theme for building jekyll sites."
  spec.homepage      = "https://github.com/KankakeeCommunityCollege/kcc-gem-theme"
  spec.license       = "MIT"

  spec.files         = `git ls-files -z`.split("\x0").select { |f| f.match(%r!^(assets|_layouts|_data|_includes|LICENSE|README)!i) }

  spec.add_runtime_dependency "jekyll", "~> 4.0.0"

  spec.add_development_dependency "bundler", "~> 2.0.1"
  spec.add_development_dependency "rake", "~> 12.0"
end
```

**Any project using the `kcc-gem-theme` that defines version that conflict with those defined in the `*.gemspec` file, will break the bundle install and build process.**
**For this reason, DO NOT COMMIT GEMFILE.LOCK INTO THE GITHUB REPO. IT CAN VERY EASILY BREAK CLOUDCANNON (and your local install).**

The following list **ARE THE DIRECTORIES CONTAINING THE FILES THAT DIRECTLY CONTRIBUTE TO THE GEM BASED JEKYLL THEME.**
**_ALL OTHER FILES/DIRECTORIES ARE IGNORED_ (expect `*.gemspec`):**
```
./ # Project root
 |-- assets/**/*
 |-- _layouts/**/*
 |-- _data/**/*
 |__ _includes/**/*
 |
 |-- LICENSE.txt ## Required for RubyGems project
 |__ README.md ## Also required
```
