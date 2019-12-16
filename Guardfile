require 'asciidoctor'
require 'asciidoctor-diagram'

guard 'shell' do
  watch(%r{^src/docs/asciidoc/(.*/)*(?!\.#)[\w\-_]+\..*$}) {|m|
    destPath = m[0].dup
    destPath[/^src/] = "build"
    FileUtils.cp m[0], destPath
  }
  watch(%r{^build/docs/asciidoc/(.*/)*(?!\.#)[\w\-_]+\.adoc$}) {|m|
    Asciidoctor.convert_file m[0], attributes: ['showtitle',
                                                'linkcss!',
                                                'source-highlighter=highlightjs'
                                                                      ]
  }
end

guard 'livereload' do
  watch(%r{^.+\.(css|js|html)$})
end

