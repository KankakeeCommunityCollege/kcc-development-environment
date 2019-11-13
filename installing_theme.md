# Installing the "kcc-gem-theme"

Install the `kcc-gem-theme` using `gem`:

```bash
gem install kcc-gem-theme
```



## Gemfile

The `kcc-gem-theme`'s version for a project is controlled by that project's Gemfile (and `Gemfile.lock`). Since the theme follows [Semantic Versioning 2.0.0](https://semver.org), The Gemfile only specifies the major version using `~>`.

```ruby
source 'https://rubygems.org'

gem 'jekyll', '~> 4.0.0'
gem 'kcc-gem-theme', '~> 1' 

```

This is essentially saying to use any version greater than `1.X.X` but lower than `2.0.0` (to avoid breaking changes in MAJOR releases).  Any breaking changes should be released as a major version anyways.

## Updates to the Theme

When updates to the `kcc-gem-theme` are created and pushed to RubyGems.org, you need to update the Gem on your local system.

The following is a brief overview of what must happen to publish changes to the `kcc-gem-theme`(Please see the `README.md` file in the `kcc-gem-theme`'s GitHub repository for a more detailed explanation).

**Yes, the order of this matters!**

1. Make the desired code changes & commit them.

2. Bump the version adhering to [SemVer2.0.0 standards](https://semver.org) and commit the `kcc-gem-theme.gemspec` file:

   ```ruby
   # frozen_string_literal: true

   Gem::Specification.new do |spec|
     spec.name          = "kcc-gem-theme"
     spec.version       = "1.18.2"  ## Version # to bump
   # More *.gemspec configuration below...
   ```

3. **Push the aforementioned commits to GitHub.**

4. Build and push the Gem:

   ```bash
   gem build kcc-gem-theme.gemspec
   ## Example output ##
   # Successfully built RubyGem
   # Name: kcc-gem-theme
   # Version: 1.18.2
   # File: kcc-gem-theme-1.18.2.gem

   gem push kcc-gem-theme-1.18.2.gem # Obviously, your gem version number will vary.
   ```

   ### Updating the Gem

   Unlike `npm` which uses a `node_modules/` dir, Gems are all installed to one location. To update your system's Gem for the `kcc-gem-theme` (which must be done after a new `kcc-gem-theme` version is released), run the following command:

```bash
gem update kcc-gem-theme
```

### Update a Projects Bundler Dependencies

The last step to updating the `kcc-gem-theme` is to update the bundle installation in each project.
