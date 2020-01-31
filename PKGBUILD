pkgname="dracut-hook"
pkgver=0.1
pkgrel=1
pkgdesc="Pacman hook for installing Dracut initramfs"
arch=('any')
url="https://www.archlinux.org/pacman/alpm-hooks.5.html"
license=('MIT')
depends=('dracut')
source=("dracut-hook"
        "60-dracut-remove.hook"
        "90-dracut-install.hook")
sha512sums=('9f7cba4d89e0f283342fef2931f06a8b2e53c4734c2db6cc5546579432a6982515b8266a1bcaaa8210f1a621b83026721f447219bf0ec1579464388460ab460a'
            'e84996806aad8ead68aa391f926f62fc8e4fff4762e5a905d9a9403fd6e1c1a40f9790830a8a15f9d46027404124ba1c561e45771f382a490e0010de76f2b7e9'
            '0d4ecd5cb2eaad2be034d5bc0108c9928a83e918604a8591601bf3ff079fb90bdfbacf1a12becdb7421dadc475ce026c33e394f7104c7501c5930fdfd969bd5f')

package() {
    install -Dm644 "${srcdir}"/*-dracut-*.hook -t "${pkgdir}"/usr/share/libalpm/hooks/
    install -Dm755 "${srcdir}"/dracut-hook     -t "${pkgdir}"/usr/share/libalpm/scripts/

    # Stop mkinitcpio from creating initramfs images
    mkdir -p "${pkgdir}"/etc/pacman.d/hooks/
    ln -s /dev/null "${pkgdir}"/etc/pacman.d/hooks/60-mkinitcpio-remove.hook
    ln -s /dev/null "${pkgdir}"/etc/pacman.d/hooks/90-mkinitcpio-install.hook
}
